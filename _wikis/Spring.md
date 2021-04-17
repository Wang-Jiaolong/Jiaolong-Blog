---
layout: wikis
title: Spring
categories: Spring
description: Spring
keywords: Spring
---

> Spring是为了解决企业级因公开发的复杂性而创建的，简化开发

# 一、Spring体系结构

![Spring的体系结构](https://i.loli.net/2021/01/08/omCJExvtg3FQ19f.gif)





# 二、Template

## spring-context.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">


</beans>
```

## web.xml

```xml
<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>classpath:spring-context*.xml</param-value>
</context-param>
<listener>
    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
</listener>
```





# 三、Spring注入Bean的方法

## 方法一：xml配置

```xml
<bean id="springContext" class="com.jiaolong.myshop.commons.context.SpringContext"/>
```

> 若使用此方法，`springContext`必须放置第一行，首先注入。

- id：在容器中查找Bean（对象）的id(唯一、且不能以/开头)
-  class：bean（对象）的完整类名
-  name：在容器中查找Bean（对象）的名字(唯一、允许以/开头、允许多个值，多个值之间用逗号或空格隔开)
-  scope:(singleton|prototype)默认是singleton
  - singleton(单例模式)：在每个Spring IoC容器中一个bean定义对应一个对象实例
  - prototype(原型模式/多例模式)：一个bean（对象）定义对应多个对象实例
- abstract：将一个bean定义成抽象bean(抽象bean是不能实例化的),抽象类一定要定义成抽象bean,非抽象类也可以定义成抽象bean
- parent：指定一个父bean(必须要有继承关系才行)
- init-method：指定bean对象（）的初始化方法
- 使用有参数构造方法创建javaBean（java对象）：constructor-arg

## 方法二：注解

**`spring-context.xml`**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd">

	<!--开启注解-->
    <context:annotation-config/>
    <context:component-scan base-package="com.jiaolong.name"/>
</beans>
```

| 注解             | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| *`@Component`    | 需要在类上使用注解`@Component`，该注解的value属性用于指定该bean的id值。 |
| *`@Repository`   | 用于对Dao实现类进行注解                                      |
| *`@Service`      | 用于对Service实现类进行注解                                  |
| *`@Controller`   | 用于对Controller实现类进行注解                               |
| `@Scope`         | 需要在类上使用，其value属性用于指定作用域。默认为singleton。 |
| `@Value`         | 需要在属性上使用，该注解的value属性用于指定要注入的值。      |
| `@Autowired`     | 需要在域属性上使用，该注解默认使用`按类型自动装配Beam`的方式。 |
| `@Resource`      | 需要在域属性上使用，该注解有`name`属性，用于创建指定bean。如`@Resource(name="userService")` |
| `@PostConstruct` | 初始化方法                                                   |



> **注解与XML配置的区别：**
>
> - 注解的好处是配置方便，只管，但是以硬编码的方式写入到了Java代码中，其修改是需要重新编译代码的。
> - XML配置方式的最大好处是，对其所做修改，无需编译代码，只需重启服务器即可将新的配置加载。
> - 若注解与XML同用，XML的优先级高于注解。这样的好处是，需要对某个Bean做修改，只需修改配置文件即可。



```xml
<!-- 使用 Annotation 自动注册 Bean，在主容器中不扫描 @Controller 注解，在 SpringMVC 中只扫描 @Controller 注解。-->
<context:component-scan base-package="com.funtl.my.shop">
    <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
</context:component-scan>
```





# 面试题

- **你是怎么理解spring的**

  Spring 的主要作用就是为代码“解耦”，降低代码间的耦合度。

  根据功能的不同，可以将一个系统中的代码分为 **主业务逻辑** 与 **系统级业务逻辑** 两类。它们各自具有鲜明的特点：主业务代码间逻辑联系紧密，有具体的专业业务应用场景，复用性相对较低；系统级业务相对功能独立，没有具体的专业业务应用场景，主要是为主业务提供系统级服务，如日志、安全、事务等，复用性强。

  Spring 根据代码的功能特点，将降低耦合度的方式分为了两类：IoC 与 AOP。IoC 使得主业务在相互调用过程中，不用再自己维护关系了，即不用再自己创建要使用的对象了。而是由 Spring 容器统一管理，自动“注入”。而 AOP 使得系统级服务得到了最大复用，且不用再由程序员手工将系统级服务“混杂”到主业务逻辑中了，而是由 Spring 容器统一完成“织入”。

  Spring 是于 2003 年兴起的一个轻量级的 Java 开发框架，它是为了解决企业应用开发的复杂性而创建的。Spring 的核心是控制反转（IoC）和面向切面编程（AOP）。简单来说，Spring 是一个分层的 Java SE/EE full-stack(一站式)轻量级开源框架。