---
layout: wikis
title: Spring
description: Spring框架是一个开放源代码的J2EE应用程序框架，由Rod Johnson发起，是针对bean的生命周期进行管理的轻量级容器。
header-img: "img/about-bg.jpg"
catalog: true
---

> Java面试题

-----

# 框架

### 1、为什么要使用spring框架？

spring 是一个开源的轻量级 JavaBean 容器框架。使用 JavaBean 代替 EJB ，并提供了丰富的企业应用功能，降低应用开发的复杂性。

- 轻量：非入侵性的、所依赖的东西少、资源占用少、部署简单，不同功能选择不同的 jar 组合
- 容器：工厂模式实现对 JavaBean 进行管理，通过控制反转（IOC）将应用程序的配置和依赖性与应用代码分开
- 松耦合：通过 xml 配置或注解即可完成 bean 的依赖注入
- AOP：通过 xml 配置 或注解即可加入面向切面编程的能力，完成切面功能，如：日志，事务...的统一处理
- 方便集成：通过配置和简单的对象注入即可集成其他框架，如 Mybatis、Hibernate、Shiro...
- 丰富的功能：JDBC 层抽象、事务管理、MVC、Java Mail、任务调度、JMX、JMS、JNDI、EJB、动态语言、远程访问、Web Service... 

### 2、什么是aop？

**AOP：Aspect Oriented Programming，面向切面编程。**
通过预编译和运行期动态代理实现程序功能的统一维护。
在 Spring 框架中，AOP 是一个很重要的功能。

AOP 利用一种称为横切的技术，剖开对象的封装，并将影响多个类的公共行为封装到一个可重用模块，组成一个切面，即 Aspect 。
"切面"就是将那些与业务无关，却为业务模块所共同调用的逻辑或责任封装起来，便于减少系统的重复代码，降低模块间的耦合度，利于可操作性和可维护性。

 

**实现 AOP 的方式，主要有两大类：**

- 采用动态代理技术，利用拦截方法的方式，对该方法进行装饰，以取代原有对象行为的执行；
- 采用静态织入的方式，引入特定的语法创建"切面"，从而使得编译器可以在编译期间织入有关"切面"的代码。

 

**AOP 相关概念**
切面（Aspect）、连接点（Join point）、通知（Advice）、切点（Pointcut）、引入（Introduction）、目标对象（Target Object）、AOP代理（AOP Proxy）、织入(Weaving)

 

spring 框架中可以通过 xml 配置和注解去使用 AOP 功能。



### 3、什么是ioc？

**IoC，Inversion of Control（控制反转）。**

是一种设计思想，在Java开发中，将你设计好的对象交给容器控制，而不是显示地用代码进行对象的创建。 

把创建和查找依赖对象的控制权交给 IoC 容器，由 IoC 容器进行注入、组合对象。这样对象与对象之间是松耦合、便于测试、功能可复用（减少对象的创建和内存消耗），使得程序的整个体系结构可维护性、灵活性、扩展性变高。

 

**使用 IoC 的好处：**

- 资源集中管理，实现资源的可配置和易管理
- 降低了资源的依赖程度，即松耦合
- 便于测试
- 功能可复用（减少对象的创建和内存消耗）
- 使得程序的整个体系结构可维护性、灵活性、扩展性变高

 

**DI**（Dependency Injection）依赖注入，是 IoC 容器装配、注入对象的一种方式。
通过依赖注入机制，简单的配置即可注入需要的资源，完成自身的业务逻辑，不需要关心资源的出处和具体实现。

 

**spring 提供了三种主要的方式来配置 IoC 容器中的 bean**

- 基于 XML 文件配置
- 基于注解配置
- 基于注解 + java 代码显式配置



### 4、spring有哪些主要模块？

1. Spring Core
   框架的最基础部分，提供 IoC 容器，对 bean 进行管理。
2. Spring Context
   基于 bean，提供上下文信息，扩展出JNDI、EJB、电子邮件、国际化、校验和调度等功能。
3. Spring DAO
   提供了JDBC的抽象层，它可消除冗长的JDBC编码和解析数据库厂商特有的错误代码，还提供了声明性事务管理方法。
4. Spring ORM
   提供了常用的“对象/关系”映射APIs的集成层。 其中包括JPA、JDO、Hibernate、MyBatis 等。
5. Spring AOP
   提供了符合AOP Alliance规范的面向方面的编程实现。
6. Spring Web
   提供了基础的 Web 开发的上下文信息，可与其他 web 进行集成。
7. Spring Web MVC
   提供了 Web 应用的 Model-View-Controller 全功能实现。





### 5、Spring Boot核心配置文件是什么？

Spring Boot 有两种类型的配置文件，application 和 bootstrap 文件
Spring Boot会自动加载classpath目前下的这两个文件，文件格式为 properties 或 yml 格式

*.properties 文件是 key=value 的形式
*.yml 是 key: value 的形式
*.yml 加载的属性是有顺序的，但不支持 @PropertySource 注解来导入配置，一般推荐用yml文件，看下来更加形象

bootstrap 配置文件是系统级别的，用来加载外部配置，如配置中心的配置信息，也可以用来定义系统不会变化的属性.bootstatp 文件的加载先于application文件
application 配置文件是应用级别的，是当前应用的配置文件

