## 概念

引用下面的一段解释spring的概念

> Spring是一个开源的轻量级Java SE（Java 标准版本）/Java EE（Java 企业版本）开发应用框架，其目的是用于简化企业级应用程序开发。应用程序是由一组相互协作的对象组成。而在传统应用程序开发中，一个完整的应用是由一组相互协作的对象组成。所以开发一个应用除了要开发业务逻辑之外，最多的是关注如何使这些对象协作来完成所需功能，而且要低耦合、高内聚。业务逻辑开发是不可避免的，那如果有个框架出来帮我们来创建对象及管理这些对象之间的依赖关系。可能有人说了，比如“抽象工厂、工厂方法设计模式”不也可以帮我们创建对象，“生成器模式”帮我们处理对象间的依赖关系，不也能完成这些功能吗？可是这些又需要我们创建另一些工厂类、生成器类，我们又要而外管理这些类，增加了我们的负担，如果能有种通过配置方式来创建对象，管理对象之间依赖关系，我们不需要通过工厂和生成器来创建及管理对象之间的依赖关系，这样我们是不是减少了许多工作，加速了开发，能节省出很多时间来干其他事。Spring框架刚出来时主要就是来完成这个功能。
>
> Spring框架除了帮我们管理对象及其依赖关系，还提供像通用日志记录、性能统计、安全控制、异常处理等面向切面的能力，还能帮我管理最头疼的数据库事务，本身提供了一套简单的JDBC访问实现，提供与第三方数据访问框架集成（如Hibernate、JPA），与各种Java EE技术整合（如Java Mail、任务调度等等），提供一套自己的web层框架Spring MVC、而且还能非常简单的与第三方web框架集成。从这里我们可以认为Spring是一个超级粘合平台，除了自己提供功能外，还提供粘合其他技术和框架的能力，从而使我们可以更自由的选择到底使用什么技术进行开发。而且不管是JAVA SE（C/S架构）应用程序还是JAVA EE（B/S架构）应用程序都可以使用这个平台进行开发

## 概念

### POJO

POJO（Plain Old Java Objects）简单的Java对象，它可以包含业务逻辑或持久化逻辑，但不担当任何特殊角色且不继承或不实现任何其它Java框架的类或接口

### Bean

一般指容器管理对象，在Spring中指Spring IoC容器管理对象。

## 核心

### IOC

Inversion of Control,即控制反转

> 对象的创建权反转(交给)给Spring，其作用是实现了程序的解耦合。也可这样解释：获取对象的方式变了。对象创建的控制权不是“使用者”，而是“框架”或者“容器”。 
> 用更通俗的话来说，IOC就是指对象的创建，并不是在代码中用new操作new出来的，而是通过Spring进行配置创建的。其底层实现原理是XML配置文件+SAX解析+工厂设计模式。 

IoC很好的体现了面向对象设计法则之一—— 好莱坞法则：“别找我们，我们找你”；即由IoC容器帮对象找相应的依赖对象并注入，而不是由对象主动去找

### AOP

Aspect Oriented Programming,即面向切片编程

>

## 配置

配置文件一般的结构

```xml
<beans>  
    <import resource=”resource1.xml”/>  
    <bean id=”bean1”class=””></bean>  
    <bean id=”bean2”class=””></bean>  
<bean name=”bean2”class=””></bean>  
    <alias alias="bean3" name="bean2"/>  
    <import resource=”resource2.xml”/>  
</beans>  
```

- <bean>标签内对Bean进行定义
- import用于导入其他配置文件的Bean定义，这是为了加载多个配置文件

- alias定义Bean别名



### xml文件

#### 自动扫描机制

在xml中增加`component-scan`标签默认情况下自动扫描指定路径下的包（含所有子包），将带有@Component、@Repository、@Service、@Controller标签的类自动注册到spring容器。

如下面的配置会将`com.eric.spring`包及子包的类自动注册

```xml
<context:component-scan base-package=”com.eric.spring
```

### Bean命名

每个Bean可以有一个或多个id（或称之为标识符或名字），在这里我们把第一个id称为“标识符”，其余id叫做“别名”；这些id在IoC容器中必须唯一

#### 约定

Bean的命名遵循XML命名规范，但最好符合Java命名规范，由“字母、数字、下划线组成“，而且应该养成一个良好的命名习惯， 比如采用“驼峰式”，即第一个单词首字母开始，从第二个单词开始首字母大写开始，这样可以增加可读性

### 实例化Bean

Spring IoC容器需要根据Bean定义里的配置元数据使用反射机制来创建Bean

主要方式有如下几种

- 使用构造器实例化Bean
- 使用静态工厂方式实例化Bean
- 使用实例工厂方法实例化Bean





![BeanFactoryãBeanDefinitionRegistryå³ç³"å¾ï¼æ¥èªï¼Springæ­ç§ï¼](https://ws4.sinaimg.cn/large/006tNc79ly1fyun9ued6qj30yg08f75e.jpg)



## 代码注解

### 分层

如果 Web 应用程序采用了经典的三层分层结构的话，最好在持久层、业务层和控制层分别采用上述注解对分层中的类进行注释

- @Service用于标注业务层组件

- @Controller用于标注控制层组件（如struts中的action）

- @Repository用于标注数据访问组件，即DAO组件

- @Component泛指组件，当组件不好归类的时候，我们可以使用这个注解进行标注。

### @Resource









resource

https://juejin.im/post/5ab0ce60518825611a405106







## 参考

- [Spring概述](http://sishuok.com/forum/blogPost/list/2426.html#7018)







