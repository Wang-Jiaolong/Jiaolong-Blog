---
layout: wiki
title: tk.mybatis
categories: tk.mybatis
description: some word here
keywords: tk.mybatis
---

> Mybatis 与 Hibernate的一个很大的区别就是Mybatis所有的数据库操作语句都需要自己写，对于简单的单表操作来说是比较烦琐的。因此有人就开发了tk.mybatis插件，通过这个插件，你可以省略许多简单的单表数据库操作语句而直接调用相对应的dao方法。

# tk.mybatis

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