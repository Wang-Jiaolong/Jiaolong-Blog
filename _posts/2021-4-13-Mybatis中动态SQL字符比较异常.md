---
layout: post
title: "「Mybatis」动态SQL字符比较异常"
subtitle: "动态sql中单个字符串比较出现异常"
author: "Jalen"
header-img: "img/about-bg.jpg"
catalog: true
tags:
  - Mybatis
  - SpringBoot
---

> 背景：为了实现动态排序，会传入一个 `+` 或`-` 来决定是正序或倒序

遇到了两个坑：单个字符无法正常比较、排序字段无法正常传参

----

## 字符无法正常比较

### 错误写法

```sql
<if test="order == '+'">
	--if同理
</if>
```

### 原因：

mybatis是使用的OGNL表达式来进行解析的，在OGNL的表达式中，'y'会被解析成字符，因为java是强类型的，char 和一个String 会导致不等。所以if标签中的sql不会被解析。

### 解决方法一：

```sql
<if test="order == '+'.toString()">
	--
</if>
```

### 解决方法二：

```sql
<if test='order == "+"'> --双引在里，单引在外
	--
</if>
```

## 2. 排序字段无法正常传参

将 `#{condition}` 改为 `${condition}` （但可能会不安全，有SQL注入风险，暂未找到合理方案）

## 完整语句

完整语句：

```sql
<choose>
    <when test="order == '+'.toString()">
        ORDER BY ${condition}
    </when>
    <otherwise>
        ORDER BY ${condition} DESC
    </otherwise>
</choose>
```