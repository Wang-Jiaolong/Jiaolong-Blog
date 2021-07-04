---
layout: wikis
title: Java
description: 一些Java常用笔记
header-img: "img/about-bg.jpg"
catalog: true
hidden: false
---



# `Math`类

## `max()`

- 参数：该方法接受两个原生数据类型作为参数。
- 返回值：返回两个参数中的最大值。

```java
public class Test{
    public static void main(String args[]){
        System.out.println(Math.max(12.123, 18.456));      
        System.out.println(Math.max(23.12, 23.0));  
    }
}

//18.456
//23.12
```
