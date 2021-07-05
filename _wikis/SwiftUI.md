---
layout: wikis
title: SwiftUI
description: SwiftUI常用
header-img: "img/about-bg.jpg"
catalog: true
hidden: false
---



#  `.animation`

- `.spring()` ：弹性
  - response: Double dampingFraction: Double, blendDuration: Double 
  - 响应时间，弹性阻力，混合模式
- `linear`：线性
- `.easeInOut`：曲线



# `Color`

- `.edgesIgnoringSafeArea(.all)`：安全区域
  - `.all`：全部



# 常见参数

- 刘海的heigh：44

-   @State var viewState = CGSize.zero  初始位置



# 语法

`@Binding` ：view间传递变量

- 不能有默认值
- 传递该状态，例：`$showProfile`





获取屏幕的尺寸

~~~swift
let screen = UIScreen.main.bounds
~~~
