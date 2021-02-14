---
layout: post
title: Servlet的doGet与doPost方法的区别与使用
categories: JavaWeb
description: The differences between doGet and doPost.
keywords: doGet, doPost , JavaWeb
topmost: false
---

## 一、调用方式

doGet：

- 直接在URL地址栏中输入URL
- 网页中的超链接
- form中method为get
- form中method为空时，默认是get提交。

doPost：

- form中method属性为post。



## 二、数据传送方式

GET方式：表单数据存放在URL地址后面。所有get方式提交时HTTP中没有消息体。数据量长度有限制，一般不超过2kb。因为是参数传递，且在地址栏中，故数据量有限制。

POST方式：表单数据存放在HTTP协议的消息体中以实体的方式传送到服务器。数量长度没有限制，适合大规模的数据传送。

## 三、安全性

GET方式：安全性差。因为是直接将数据显示在地址栏中，浏览器有缓冲，可记录用户信息。所以安全性低。

POST方式：安全性高。因为post方式提交数据时是采用的HTTP post机制，是将表单中的字段与值放置在HTTP HEADER内一起传送到ACTION所指的URL中，用户是看不见的。



## 四、刷新页面

GET方式：不会有任何提示、

POST方式：会弹出提示框，问用户是否重新提交。