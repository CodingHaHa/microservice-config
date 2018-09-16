

# 一、SpringBoot入门

![1537108962920](C:\Users\FengLian\AppData\Local\Temp\1537108962920.png)

## 1、SpringBoot简介

>简化Spring应用开发的一个框架；
>
>整个Spring技术的一个大融合；
>
>也是我们javaEE开发的一站式解决方案；

## 2、SpringBoot优缺点

### 优点

> 快速创建独立运行的Spring项目以及与主流框架集成
>
> 使用嵌入式的Servlet容器，应用无需打成WAR包
>
> starters自动依赖与版本控制
>
> 大量的自动配置，简化开发，也可修改默认值
>
> 无需配置XML，无代码生成，开箱即用
>
> 准生产环境的运行时应用监控
>
> 与云计算的天然集成

### 缺点

> 就是入门容易，精通难，它需要对Spring底层的原理，API，注解有一定的掌握



## 3、什么是微服务？

![1537109061338](C:\Users\FengLian\AppData\Local\Temp\1537109061338.png)

2014年，martin fowler发表了一篇有关微服务的论文；

### ①：单体应用

![1537109412581](C:\Users\FengLian\AppData\Local\Temp\1537109412581.png)

#### 优点

> 所有的功能都放到一个项目中，项目的开发、测试、部署、与水平扩展都是比较简单的；
>
> - **为人所熟知**：现有的大部分工具、应用服务器、框架和脚本都是这种应用程序；
> - **IDE****友好**：像NetBeans、Eclipse、IntelliJ这些开发环境都是针对开发、部署、调试这样的单个应用而设计的；
> - **便于共享**：单个归档文件包含所有功能，便于在团队之间以及不同的部署阶段之间共享；
> - **易于测试**：单体应用一旦部署，所有的服务或特性就都可以使用了，这简化了测试过程，因为没有额外的依赖，每项测试都可以在部署完成后立刻开始；
> - **容易部署**：只需将单个归档文件复制到单个目录下。

#### 缺点

> 牵一发而动全身，任何地方出现
>
> 1. 先天性缺陷：难以分布式部署和扩容 
> 2. 系统性风险：一个组件的缺陷导致真个进程崩溃 
> 3. 运维风险：系统升级、Bug修复、故障排查存在风险
> 4. 难以可持续发展：业务范围拓展后，难以复用原有的服务，又要重新开发 

### ②：微服务

#### 参考文档 

[[微服务文档]](https://martinfowler.com/articles/microservices.html)



![1537109677486](C:\Users\FengLian\AppData\Local\Temp\1537109677486.png)



>一个应用应该是一组小型服务；每个服务运行在自己的进程中，微服务之间可以通过轻量级的通信机制，通常是HTTP的方式进行通信；并且这些服务是独立部署的；可以实现语言无关性；也可以使用自己独立的数据存储；



#### 优点

>- 易于开发、理解和维护；
>- 比单体应用启动快；
>- 局部修改很容易部署，有利于持续集成和持续交付；
>- 故障隔离，一个服务出现问题不会影响整个应用；
>- 不会受限于任何技术栈。
>- 每个微服务可以由不同的团队独立开发。
>- 微服务是松散耦合的。



#### 缺点

>**运维成本过高**
>
> **代码重复** 
>
>**分布式系统的复杂性** 
>
>**接口不匹配** :服务依赖于彼此间的接口进行通信。改变一个服务的接口会对其他服务造成影响
>
>**异步** :微服务常常会使用异步编程、消息与并行，如果要求某个操作必须是同步且具有事务的，那么这就非常复杂了，这要求我们得“管理好相关联的ID以及分布式事务，将各种动作绑定在一起”。  
>
>**测试** :使用微服务架构时，测试是另一个需要考虑的问题，因为“无论是手工测试还是自动化测试，我们都很难以一致的方式重现环境”， 



微服务的具体图：

![1537110480421](C:\Users\FengLian\AppData\Local\Temp\1537110480421.png)



#### SpringBoot与微服务

![1537110742516](C:\Users\FengLian\AppData\Local\Temp\1537110742516.png)



![1537110760936](C:\Users\FengLian\AppData\Local\Temp\1537110760936.png)



## 4、环境准备

学习SpringBoot需要掌握如下的内容

>–Spring框架的使用经验
>–熟练使用Maven进行项目构建和依赖管理
>–熟练使用Eclipse或者IDEA



环境

>–jdk1.8:SpringBoot官方推荐1.7及以上版本
>–maven3.x：最好maven3.3以上版本
>–IntelliJ IDEA 2017
>–Spring Boot 1.5.9.RELEASE



### 1、Maven设置

给maven的settings.xml配置文件的<profiles>添加如下代码；

**它告诉Maven使用JDK1.8来编译和运行程序**

```
<profile>
  <id>jdk-1.8</id>
  <activation>
    <activeByDefault>true</activeByDefault>
    <jdk>1.8</jdk>
  </activation>
  <properties>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
    <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
  </properties>
</profile>
```



### 2、配置IDEA中Maven配置

![1537111463571](C:\Users\FengLian\AppData\Local\Temp\1537111463571.png)



##5、SpringBoot的HelloWorld项目

功能描述：

​	浏览器发送hello请求，服务器接收	请求并处理，响应Hello World字符串



[详情参考官网文档](https://docs.spring.io/spring-boot/docs/1.5.9.RELEASE/reference/html/)



### ①、创建一个Maven工程

![1537111692557](C:\Users\FengLian\AppData\Local\Temp\1537111692557.png)



![1537111771390](C:\Users\FengLian\AppData\Local\Temp\1537111771390.png)



![1537111797711](C:\Users\FengLian\AppData\Local\Temp\1537111797711.png)



###②、导入SpringBoot的依赖

参考SpringBoot官网的QuickStart

```
    <!-- Inherit defaults from Spring Boot -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.9.RELEASE</version>
    </parent>

    <!-- Add typical dependencies for a web application -->
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
```



### ③、编写一个主程序；它用于启动SpringBoot应用

![1537112263630](C:\Users\FengLian\AppData\Local\Temp\1537112263630.png)

IDEA在创建类的时候写上包名，就会自动创建包；

```
package com.feng;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

/**
 * @author FengLian
 * @create 2018/9/16
 * 描述:
 *  @SpringBootApplication ：用于标注一个主程序类，说明这是一个SpringBoot应用
 */
@SpringBootApplication
public class HelloWorldMainApp {

    public static void main(String[] args) {
        /**
         * SpringApplication.run()：该函数
         *          参数一：是当前的主程序类名
         *          参数二：当前main函数的参数
         */
        SpringApplication.run(HelloWorldMainApp.class,args);
    }
}
```



###④、编写相关的Controller、Service

```
@Controller
public class HelloController {
    @RequestMapping("/hello")
    @ResponseBody
    public String hello(){
        return "Hello World";
    }
}
```



### ⑤、直接运行主函数，就能启动这个SpringBoot应用





###⑥、SpringBoot应用可以简化项目的部署工作

[参考文档](https://docs.spring.io/spring-boot/docs/1.5.9.RELEASE/reference/html/getting-started-first-application.html#getting-started-first-application-executable-jar)

在当前项目的pom.xml文件中导入如下内容

```
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

```
这个插件可以实现将应用打包成一个可执行的jar包

***打包时它会内嵌一个Servlet容器；***
```

![1537113022083](C:\Users\FengLian\AppData\Local\Temp\1537113022083.png)





![1537113075792](C:\Users\FengLian\AppData\Local\Temp\1537113075792.png)





![1537113150308](C:\Users\FengLian\AppData\Local\Temp\1537113150308.png)

