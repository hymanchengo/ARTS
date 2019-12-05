### 容器,依赖和控制反转
 - 什么是依赖注入，优点是什么
 - 接口是什么，在Java中使用接口有什么优点
     
        为什么推荐它们用于Spring beans
 - 应用程序上下文是什么意思
 - 怎么创建一个ApplicationContext实例
 - ApplicationContext中的Spring Bean的生命周期
 - 集成测试环境中如何创建ApplcationContext
 - 关闭一个Application context的首选方式是什么？Spring Boot会做这件事吗
 - 描述下：
        
        使用Java配置实现的依赖注入
        
        使用注解(@Autowired)实现的依赖注入
        
        组件扫描，Stereotypes
        
        Spring beans的作用域。默认的作用域是什么
  - beans默认是预加载还是懒加载的？如何修改这个行为
  - property source是什么？ 怎么使用@PropertySource
  - BeanFactoryPostProcessor是什么，它的用途是什么？它何时被调用
      
          定义一个静态@Bean方法的理由是？
          
          ProperySourcePlaceholderConfigurer的用途是？
          
  - BeanPostProcessor是什么？它和BeanFactoryPostProcessor有何不同？它们的用途？它们何时被调用
          
          initialization方法的用途，它是如何声明在Spring bean上的
          
          destroy方法的用途，它是怎么声明的，什么时候被调用
            
            - 如果你启用了JSR-250注解比如@PostConstruct和@PreDestroy？它们何时及如何被调用？
            
            - 还可以怎样为一个Sprinbg Bean定义一个初始化或销毁方法
            
  - component-scanning的用途是什么
       
  - 对于字段注入，构造函数注入和方法注入，@Autowired注解的行为分别是什么
       
  - 如果要将某个啥注入到一个私有字段，必须做什么？这将会如何影响测试？
       
  - @Qualifier注解如何结合@Autowired使用
       
  - 代理对象是什么，Spring可以创建的两种不同类型的代理对象是什么？
          
          这两种代理类型的对象各自的限制是什么
          
          代理对象的能力及缺点分别有哪些
  - @Bean注解的作用
  - 如果只使用@Bean，默认的bean id是什么？怎么重写它？
  - 为什么不允许在final类上使用@Configuration注解
      
         @Configuration注解类是怎么支持单例beans的
         
         为什么@Bean方法也不能是final的
   - 怎么配置配置文件？它们可能有用的使用场景是什么
   - @Bean和@Profile能一起使用吗
   - @Component和@Profile能一起使用吗
   - 可以有多少配置文件
   - 如何将scalar/literal值注入Spring beans？
   - @Value的作用
   - 什么是SPring Expression Language（SpEL）
   - Spring中的Environment抽象是什么
   - 环境中的属性来自哪里-属性有许多来源-如果不确定可以查看文档。Spring Boot添加了更多
   - 使用SpEL可以引用什么？
   - $和#符号在@Value表达式中的区别是什么？
