### Algorithm



### Review
  文章 [How Reliable Are Product Ratings?](https://onezero.medium.com/how-reliable-are-product-ratings-2fed46b76805)
  翻译 
### Tip 学习至少一个技术技巧

### Share 分享一篇有观点和思想的技术文章

      第一次加入ARTS，有点纠结ARTS的每个字母的含义，对于技术文章，我仔细斟酌着什么才算技术文章，但我想
    
    ARTS不局限于内容，更在于它的目的。因此如果我摘选的内容偏离了ARTS主题，希望不会让大家不开心，毕竟
    
    我记得ARTS注重的是参与而不是围观，因此权且当这里是一个监督自己和积累的地方。
    
      说起来现在工作接触到java,但却不是每天都写Java代码，当然这其中主要的原因在自己，缺少合理的规划和坚持。还是有点
      
     哪边急补哪边知识的意思。我是乘着Spring Boot的春风，才转回Java的，Java技能少得可怜。虽然Spring Boot会用会写，
     
     但总觉得心里没底，因此总惦记着要学Spring。怎么学？ 这次我希望借ARTS的机会，先试试翻译翻译官方文档，尽量写点demo，
      
     然后尽量做点总结和思考。这也是之前没有尝试过的。以前自学就是看书，然后敲示例代码，然后结束，但是没有自己的思考，
      
     纸上得来总觉浅啊。
     
       今天上Spring官网看到有个Spring Professional certification exams，我转念一想，在浏览Spring文档前，先看看这里面要
       
     考查的知识点。应该会对后续的学习有点帮助，因此将里面的内容尝试翻译些许。
     
     容器,依赖和控制反转
     - 什么是依赖注入，优点是什么
     - 接口是什么，在Java中使用接口有什么优点
     
        为什么推荐它们用于Spring beans
     - 应用程序上下文是什么意思
     - 你会怎么创建一个ApplicationContext实例
     - 你能描述下ApplicationContext中的Spring Bean的生命周期吗
     - 集成测试环境中你会怎么创建ApplcationContexdt
     - 关闭一个Application context的首选方式是什么？Spring Boot会做这件事吗
     - 你能描述下：
        
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
       
       - 字段注入，构造函数注入和方法注入，@Autowired注解的行为是什么
       
       - 如果要将某个啥注入到一个私有字段，必须做什么？这将会如何影响测试？
       
       - @Qualifier注解如何结合@Autowired使用
       
       - 代理对象是什么，Spring可以创建的两种不同类型的代理对象是什么？
          
          这两种代理类型的对象各自的限制是什么
          
          代理对象的能力及缺点分别有哪些
       
          
        
        
      
      
