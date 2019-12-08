## 依赖
### 依赖的上下文是什么？
依赖这个词的语境是什么？它描述的是什么之间的依赖？为什么会有依赖？

我们依赖空气，水，孩子依赖父母。那么本主题谈论的依赖，它的上下文是什么？ 

先看Spring官网的一段描述

一个典型的企业应用不是由单一对象（Spring称为bean）构成的。

即使最简单的应用程序都有一些对象协作来呈现给终端用户视为一致的应用。

因此这边的依赖描述的是对象之间的依赖，即bean之间的依赖。因为一个应用不是一个对象独立构建的，

多个对象共同作用，这边就产生了一个对象依赖另一个对象的问题。

### 依赖注入 Dependency injection（DI） 
- 概念
      
      依赖注入是一个过程，通过这个过程，对象只能通过构造函数参数，工厂方法的参数，

      或在构造完成后或工厂返回的对象实例上的属性上设置依赖。然后容器在

      创建bean时，将这些依赖注入进来。这个过程根本上是bean通过直接构造类或通过服务定位模式来

      自己控制依赖的初始化和位置的逆过程。因此叫控制反转。

- 优点

      代码更加整洁。解耦更加有效。对象不查找它的依赖项并且不知道依赖的类或位置。
      
      类变得更容易测试，尤其是依赖的是接口或抽象基类，这样在单元测试中可以使用
      
      模拟的实现。
      
- 变体
    
      1.基于构造函数的依赖注入
            通过容器调用多个参数的构造函数实现，每个参数代表一个依赖。
            调用带有特定参数的静态工厂方法来构造bean几乎是等效的
            这边认为构造函数和静态工厂方法的参数是相同的
```java
// 基于构造函数的依赖注入
public class SimpleMovieLister {
    
    // SimpleMovieLister依赖MovieFinder
    private MovieFinder movieFinder;

    // 构造函数,Spring容器可以注入MovieFinder实例
    public SimpleMovieLister(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    //使用注入的MovieFinder的业务逻辑代码(略)
}
```
         这是一个POJO,没有以来任何容器特定接口，基类或注解。
         
      2.基于Setter的依赖注入
 - 构造参数解析
      
      构造函数参数解析匹配通过使用参数类型进行。如果bean的构造参数中不存在潜在的二义性，
      
      bean构造函数中定义的参数顺序就是实例化bean时提供给合适的构造函数的参数的顺序。
```java
package x.y;

public class ThingOne {
    public ThingOne(ThingTwo thingTwo, ThingThree thingThree) {
        
    }
}
```
      假定ThingTwo和ThingThree没有继承关系，没有潜在的二义性存在。以下配置可以正常工作，
      
      无需在<constructor-arg>元素中显式地指定构造函数参数索引或者类型
```xml
<beans>
    <bean id="beanOne" class="x.y.ThingOne">
        <constructor-arg ref="beanTwo"/>
        <constructor-arg ref="beanThree"/>
    </bean>

    <bean id="beanTwo" class="x.y.ThingTwo"/>

    <bean id="beanThree" class="x.y.ThingThree"/>
</beans>
```
当另一个bean被引用，已知类型，匹配就会发生。当使用一个简单类型时，比如<value>true</value>。Spring
不能确定值的类型，不干预的话无法匹配
```java
package examples;
public class ExampleBean {
    
    // 计算Ultimate Answer的年数
    private int years;

    // 生命，宇宙和任何其他事的答案
    private String ultimateAnswer;

    public ExampleBean(int years, String ultimateAnswer) {
        this.years = years;
        this.ultimateAnswer = ultimateAnswer;
    }
} 
```
      ** 构造函数参数类型匹配 **
      在上面这种情况下，使用type属性显式指定构造函数参数类型后，容器可以使用类型匹配
```xml
<beans>
    <bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg type="int" value="7500000"/>
        <constructor-arg type="java.lang.String" value="42"/>
    </bean>
</beans>
```
      ** 构造函数参数索引 **
      可以使用index属性来显式指定构造函数参数的索引
```xml
<bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg index="0" value="7500000">
        <constructor-arg index="1" value="42">
</bean>
```
      除了解决多个简单值的二义性外，指定index解决构造函数有相同类型的2个参数的二义性
      
      index是基于0的
      
      ** 构造函数参数名称 **
      可以使用构造函数参数名称来消除二义性
```xml
<bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg name="years" value="7500000">
        <constructor-arg name="ultimateAnswer" value="42">
</bean>
```
      记住，要开箱即用，代码编译时必须启用debug标志，这样Spring可以从构造函数中查找名称。如果不想要开启
      
      debug标志编译代码，可以使用@ConstructorProperties JDK注解来显式命名构造函数参数
      
      看起来像下面这样
 ```java
 @ConstructorProperties({"years", "ultimateAnswer"})
    public ExampleBean(int years, String ultimateAnswer) {
        this.years = years;
        this.ultimateAnswer = ultimateAnswer;
    }
 ```
 

