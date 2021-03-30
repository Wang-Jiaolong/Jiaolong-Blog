---
layout: wiki
title: MyBatis
categories: MyBatis
description: MyBatis
keywords: MyBatis
---

> MyBatis 是一个优秀的基于 Java 的持久层框架，它内部封装了 JDBC，使开发者只需关注 SQL 语句本身，而不用再花费精力去处理诸如注册驱动、创建 Connection、配置 Statement 等繁杂过程。

# Mybatis

> Mybatis 通过 xml 或注解的方式将要执行的各种 Statement（Statement、PreparedStatement 等）配置起来，并通过 Java 对象和 Statement 中 SQL 的动态参数进行映射生成最终执行的 SQL 语句，最后由 MyBatis 框架执行 SQL 并将结果映射成 Java 对象并返回。

![aaa](https://i.loli.net/2021/01/13/7H8efpjhWXxKVFB.png)







## MyBatis特点

![aaa](https://i.loli.net/2021/01/13/rSKLsbUtVO4M1Dx.png)





# tk.mybatis

Mybatis 与 Hibernate的一个很大的区别就是Mybatis所有的数据库操作语句都需要自己写，对于简单的单表操作来说是比较烦琐的。因此有人就开发了tk.mybatis插件，通过这个插件，你可以省略许多简单的单表数据库操作语句而直接调用相对应的dao方法。在SSM项目中配置和使用tk.mybatis插件的用法如下：
1、在pom.xml文件中引入依赖

```xml

<tk.mybatis.verson>3.3.7</tk.mybatis.verson>
<persistence.version>1.0</persistence.version>


<dependency>
    <groupId>tk.mybatis</groupId>
    <artifactId>mapper</artifactId>
    <version>${tk.mybatis.verson}</version>
</dependency>
<dependency>
    <groupId>javax.persistence</groupId>
    <artifactId>persistence-api</artifactId>
    <version>${persistence.version}</version>
</dependency>
```