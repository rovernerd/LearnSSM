## SpringBoot

本文主要介绍了SpringBoot的基础知识

### 介绍

Spring Boot是来简化Spring应用的开发

- SpringBoot => J2EE一站式解决方案

- SpringCloud=>分布式整体解决方案

### 优点

- 快速创建独立运行的Spring项目，与主流框架快速集成
- 使用嵌入式Servlet容器，应用无需打成WAR包
- Starters自动依赖与版本控制(JDBC/Redis)
- 准生产环境的运行时应用监控

### 缺点

入门容易，精通较难，需要对底层的spring有较高的理解.

## 时代背景

### 维服务(microservice)

2014年martin fowler提出，发表维服务的文章.

### 概念

阐述了开发的架构风格，维服务架构风格应该是一组小服务(a suite of small services),通过HTTP的方式进行互通.

### 和单体应用对比

单体应用:ALL IN ONE  

#### 优点

- 测试简单

- 便于部署

- 水平扩展简单

### 理念

复制的不是整个服务，而是功能元素，组合更加灵活多变.

每一个功能元素最终都是一个可独立替换和独立升级的软件单元





## 使用

### 环境统一

如下几个要点

- SpringBoot 1.5.9

- Maven设置

配置文件中添加如下配置，指定编译使用的jdk版本

- IDEA引用maven设置

Configure => 

Preference => 

Build,Execution,Deployment =>

Build Tools =>

Maven =>

Maven home dictionary => `自己的maven安装路径`

### 需求

浏览器发送hello请求，服务器接受并处理，响应浏览器请求

### 步骤

#### 1.创建maven工程(jar包)

#### 2.导入springboot相关的依赖

```xml
<parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.9.RELEASE</version>
</parent>

<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```

### 3.编写主程序,启动spring boot app

```java
/**
 * @SpringBootApplication 注明这是一个springboot应用
 */

@SpringBootApplication
public class HelloWorldMainApplication {

    public static void main(String[] args) {

        // spring启动程序
        SpringApplication.run(HelloWorldMainApplication.class,args);


    }

}
```

####  4.编写相关的Controller、Service

```java
@Controller
public class HelloController {

    @ResponseBody
    @RequestMapping("/hello")
    public String hello(){
        return "helloworld";
    }

}
```

#### 5.运行主程序启动(main方法)

在浏览器访问`localhost:8080/hello`，可以看到浏览器返回了helloworld

#### 6.简化部署

在pom中加入插件，可以打包成一个可执行的jar包

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```



快速打包方法

Maven Projects =>

lifeCycles=>

Packages



打包完成后可以直接执行`java -jar xxx.jar`去启动.

具体可以参考

[Creating an executable jar](https://docs.spring.io/spring-boot/docs/1.5.19.RELEASE/reference/htmlsingle/#getting-started-first-application-executable-jar)



Ps:

在打包时自行打入了imbeded的tomcat, 目标服务器不用部署tomcat

























