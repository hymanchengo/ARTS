### 数据管理：JDBC，事务
- 验证过和非验证过的异常区别是什么
      
      为什么Spring倾向未验证异常
      数据访问异常的层次是什么
 - 在Spring中如何配置数据源？哪个bean对于开发/测试数据库很有用
 - 模板的设计模式是什么？什么是JDBC模板
 - 什么是回调？可用于查询的3个JDBCTemplate回调接口是什么？每个用在什么场景
 - 使用JDBC template是否可以执行普通SQL语句
 - JDBC template什么时候需要和释放一个连接，每个方法调用或每个模板一次调用？为什么？
 - JdbcTemplate是怎么支持泛型查询的？它是怎么返回对象和对象列表/对象Maps的
 - 什么是事务？局部和全局事务的区别是什么？
 - 事务是横切关注分离的吗？Spring是怎么实现它的？
 - 在Spring中怎么定义一个事务
      
      @Transactional的用途？PlatformTransactionManager的用途
 - JDBC模板是否能加入一个现有事务
 - 什么是事务隔离级别？有几个级别，他们是怎么排序的
 - @EnableTransactionManagement的用途是？
 - 事务传播是什么意思？
 - 一个对象实例上的一个@Transactional注解方法调用该实例上的另一个@Transactional注解方法会发生什么
 - @Transactional注解可以用在哪？放在类级别的典型用途是什么？
 - 声明式事务管理意味者什么
 - 默认的回滚策略是什么？怎样重写？
 - 当在JUnit4中使用@RunWith(SpringJUnit4ClassRunner.class) 或者在Junit5中使用@ExtendWith(SpringExtension.class)，及使用
   @Transactional注解你的@Test注解方法时，JUnit测试的默认回滚策略是什么？
 - 工作单元模式为什么如此重要，为什么JDBC AutoCommit违反了这个模式
 - Spring中如何使用JPA
 - 在Spring中使用JPA时是否能加入到给定的事务中
 - JPA可以使用哪个PlatformTransactionManager(s)
 - Spring中使用JPA如何配置？Spring Boot如何简化它的
 
 
 
