---
title: "「IDEA」去掉IntelliJ IDEA生成的mybatis映射文件中黄色和绿色的背景"
subtitle: "IntelliJ IDEA 打开 mybatis 的 xml 文件时，对应的 xml 文件中 sql 语句背景色总是有黄色或绿色的背景色。"
layout: post
author: "Jalen"
header-style: text
hidden: false
tags:
  - IDEA
---

> IntelliJ IDEA 打开 mybatis 的 xml 文件时，对应的 xml 文件中 sql 语句背景色总是有黄色或绿色的背景色。

### 1. 去掉 `No data sources configure` 警告

> 原因：没有配置数据源运行此 SQL

解决方法：

- 方法一：配置data source

- 方法二：取消提示显示 `Prefernces` ⇒ `Editor` ⇒ `Inspections`⇒ `SQL` ⇒ `No data sources configure`  ⇒ 去掉对勾

  ![Untitled](https://i.loli.net/2021/04/13/1cUvRgqZ5taMzpD.png)

### 2. 去掉 `SQL dialect is not configured` 警告

> 原因：Idea能自动给我们检查拼接的sql语句的语法正确性，当然需要进行一定的配置。

解决方案：

方法一：配置 `Generic`，设置其 `dialect`

方法二：

- `Prefernces`⇒ `Editor`⇒ `Inspections`⇒ `SQL`⇒ `SQL dialect detection`  ⇒ 去掉对勾

- 取消勾选，去掉这个检查，然后点击 `OK` 按钮即可。

  ![Untitled](https://i.loli.net/2021/04/13/WrQOwmaD4IgslHN.png)

### 3. 去掉“注入语言”的背景色

`Prefernces` ⇒ `Editor` ⇒ `Colors & Fonts` ⇒ `General` ⇒ `Code` ⇒ `Injected lnguage fragment` ⇒ `Background`  ⇒ 去掉对勾

![Untitled](https://i.loli.net/2021/04/13/Egwx6AefNSJHWB3.png)