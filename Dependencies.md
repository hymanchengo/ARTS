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
    
#### 基于构造函数的依赖注入
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
   构造函数参数类型匹配
   
      在上面这种情况下，使用type属性显式指定构造函数参数类型后，容器可以使用类型匹配
```xml
<beans>
    <bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg type="int" value="7500000"/>
        <constructor-arg type="java.lang.String" value="42"/>
    </bean>
</beans>
```
   构造函数参数索引
      
      可以使用index属性来显式指定构造函数参数的索引
```xml
<bean id="exampleBean" class="examples.ExampleBean">
        <constructor-arg index="0" value="7500000">
        <constructor-arg index="1" value="42">
</bean>
```
      除了解决多个简单值的二义性外，指定index解决构造函数有相同类型的2个参数的二义性
      
      index是基于0的
      
   构造函数参数名称
   
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
 #### 基于Setter的依赖注入
 基于Setter的依赖注入是调用无参构造函数或无参静态工厂方法实例化bean之后，容器在bean上调用setter方法来实现的
 ```java
 // 基于Setter方法的依赖注入
public class SimpleMovieLister {
    
    // SimpleMovieLister依赖MovieFinder
    private MovieFinder movieFinder;

    // Setter方法 Spring容器注入MovieFinder实例
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    //使用注入的MovieFinder的业务逻辑代码(略)
}
 ```
 ApplicationContext支持其管理的bean基于构造函数和基于Setter方法进行依赖注入。
 
 它也支持在一些依赖已经通过构造函数方式注入后使用基于Setter的依赖注入
 
 以BeanDefinition的形式配置依赖，结合PropertyEditor实例将属性从一种格式转换为另一种
 
 然而，大多数Spring用户不会直接用这些类（就是以编程的方式）,而是用XML bean定义，
 
 或注解组件（比如使用@Component,@Controller等注解类）,或者在基于Java的@Configuration类里
 
使用@Bean方法。这些来源然后在内部被转换为BeanDefinition的实例，用来加载整个Spring IoC 容器实例。
      
      基于构造函数还是Setter方法进行依赖注入?
      
      因为可以混合使用基于构造函数和基于setter方法的依赖注入，经验来说使用为强制依赖使用构造函数
      
      可选依赖使用setter方法或配置方法。注意，在setter方法上使用@Required注解可使属性成为一个必须依赖。
      
      但是最好使用带有参数程序性验证的构造函数依赖注入
      
      Spring团队通常提倡使用构造函数方式注入，因为它可以将应用程序组件实现为不可变的对象，
      
      并确保所需的依赖项不为null。而且，构造方式注入的组件总是返回给调用者代码完全初始化的状态。
      
      题外话，大量构造函数参数是代码坏味，暗示类可能有太多职责，应该被重构以更好地解决关注点分离问题
      
      基于Setter注入应该主要只用在可以在类中分配合理默认值的可选依赖。否则，非null检查必须在代码使用
      
      依赖的每处地方执行。Setter注入的一个好处是setter方法可使类的对象在以后可以重新配置或重新注入。
      
      通过JMX Mbeans进行的管理是一个典型的setter注入使用案例
      
      使用对一个特定类最有意义的依赖注入风格，有时处理第三方你没有源码的类，已经不需要你选择了。
      
      比如如果第三方类没有暴露任何setter方法，构造注入可能是依赖注入的唯一可用形式。
      
- 依赖解析过程
     容器执行bean的依赖解析如下：
     - ApplicationContext创建并用描述了所有beans的配置metadata进行初始化。配置metadata可以被
     
     XML或Java代码或注解指定。
     
     - 每个bean，它的依赖以属性，构造函数参数或静态工厂方法的参数的形式表示。当bean实际创建时，这些依赖会提供给bean
     
     - 每个属性或构造函数参数是要设定的值或容器中另一个bean的引用的实际定义
     
     - 每个属性或构造函数参数是一个从指定格式转换为属性或构造函数参数的实际类型的值。默认情况下，
     
     Spring可以将以String格式提供的值转换成任何内置类型，比如int,long,String,boolean等。
     
     创建容器时,Spring容器会验证每个bean的配置。然而bean的属性本身直到bean被创建时才会设定。
     
     单例作用域的bean和被设定为预初始化(默认)的bean在容器创建时随之创建。作用域是定义在
     
     Bean Scopes里的。其他情况下，当bean被用到时才会创建。一个bean的创建可能会引起一堆bean的创建，
     
     因为bean的依赖和依赖的依赖被创建和指定。注意这些依赖间的解析不匹配可能出现得较晚——就是在受影响bean第一次创建时
     
    **循环依赖**
            
            如果主要使用构造函数注入，可能会发生无法解决的循环依赖场景
            
            比如A类构造函数注入需要B类，B构造函数注入依赖A，如果为A类和B类配置互为注入的Bean，Spring IoC容器
            
            在运行时会检测到循环引用，扔出BeanCurrentlyInCreationException异常
            
            一个可行的解决方案是编辑一些类的源代码使用setters注入而不是构造函数注入。换句话说
            
            尽管不推荐，但是setter注入可以配置循环依赖
            
            和一般情况(没有循环依赖的情况)不同,Bean A 和 Bean B之间的循环依赖迫使其中一个bean在完全初始化自身之前
            
            就被注入到另一个Bean中（经典的鸡生蛋场景）
    
  一般Spring都会把好关。在容器加载期间，它会监测配置问题，比如引用一个不存在的bean和循环依赖。Spring尽可能迟地
  
  设置属性和解析依赖，直到bean创建的时候。这意味着即便spring容器正确加载，当请求使用一个对象时创建这个对象或它的
  
  依赖时出现问题时会稍后产生异常。比如由于缺少属性或属性不合理，bean丢出异常。这潜在地推迟了一些配置问题的暴露。
  
  这也是ApplicationContext实现为什么默认预初始化单例beans的原因。以一些前期时间和内存为代价在实际需要它们前
  
  创建这些beans，换来的是在ApplicationContext创建的时候就能发现配置问题而不是在后面。仍然可以改写这种默认行为让
  
  单例beans懒加载。
  
  当没有循环依赖存在时，一个或多个协作的beans被注入到依赖的bean里，每个协作bean在被注入到依赖的bean之前都是完全配置的
  
  这意味如果A依赖Bean B，Spring IoC容器在调用bean A的Setter方法前完全装配bean B。换句话说，bean已初始化好（如果不是预初始化的
  单实例bean），它的依赖也设定了。相关的生命周期循环方法被调用（比如配置初始化方法或初始Bean回调方法）
            



 
 

