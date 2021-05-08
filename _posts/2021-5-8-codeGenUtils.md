---
layout:     post
title:      "「Utils」验证码生成工具类"
subtitle:   "用于随机生成n位验证码 "
author:     "Jalen"
header-img: "img/about-bg.jpg"
catalog: true
tags:
    - Utils
---

> Json和List、Map之间的相互转换

-----

> 随机生成n位验证码

<!--more-->

## `Java`

```java
    /**
     * 随机验证码
     * @param number 位数
     * @return
     */
    public String codeGen(int number) {
        char[] codeSequence = {'A', 'B', 'C', 'D', 'E', 'F', 'G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z','0', '1', '2', '3', '4', '5', '6', '7', '8', '9'};
        //动态字符串
        StringBuilder sb = new StringBuilder();
        Random random = new Random();
        int count = 0;
        while (true) {
            int index = random.nextInt(codeSequence.length); //定义随机数的范围并且产生一个随机的下标
            //随机的取出一个数
            char c = codeSequence[index];
            if (sb.indexOf(c + "") == -1) { //不让字符重复,并且把一个字符变成字符串
                sb.append(c);
                count++;
                if (count == number) {   //设置位数
                    break;
                }
            }
        }
        return sb.toString();
    }
```


