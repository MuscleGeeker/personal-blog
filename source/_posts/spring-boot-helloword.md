---
title: 【Hello Spring Boot】之HelloWorld
date: 2017-08-24 11:19:15
tagsi: Spring Spring Boot Restful Web Java
---
# 简介
## Spring Boot的主要优点：

* 为所有Spring开发者更快的入门
* 开箱即用，提供各种默认配置来简化项目配置
* 内嵌式容器简化Web项目
* 没有冗余代码生成和XML配置的要求

-------
# 快速入门
## 系统要求
* Java7及以上
* Spring Framework 4.1.x及以上

## 使用maven构建项目
* 使用Spring官方Spring Initializer工具生成基础项目

```
访问：http://start.spring.io/
选择构建工具、开发语言类型、Spring Boot版本、输入工程基本信息
点击Generate Project
```
![](http://ounvdrscf.bkt.clouddn.com/001.png)

* 解压项目包，并将项目导入IDE中(以idea为例)
    
```
菜单中选择File->New->Project From Existing Sources...
选择项目解压后的文件夹，找到对应的pom.xml文件，一路Next
(注意jdk要选择1.7以上版本)
```
通过上面的步骤完成基本项目的创建，对项目的结构进行相应的更改后，变成下图所示的项目结构：
![](http://ounvdrscf.bkt.clouddn.com/blog002.png)

## 项目结构解析

```
src/main/java 程序的入口*****Application.java
src/main/resources 程序的配置文件application.properties
```
生成的Application类可以直接运行启动当前创建的项目，但是由于该项目没有设置任何数据访问和Web模块，程序会再加载完后结束运行。
## 引入Web模块
通过当前项目的pom.xml文件引入两个模块

```
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter</artifactId>
    </dependency>
    
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```

## 编写helloworld服务

```
创建包controller用来存放控制器类
新建控制器类HelloController

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "Hello World!";
    }
}

启动主程序，打开浏览器访问http://localhost:8080/hello,可以看到页面输出Hello World!
```

至此已完成目标：通过Maven构建了一个空白Spring Boot项目，再通过引入web模块实现了一个简单的请求处理。
