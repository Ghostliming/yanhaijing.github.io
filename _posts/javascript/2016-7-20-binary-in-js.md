---
layout: post
title: 聊聊JavaScript中的二进制数
category : javascript
tagline: "原创"
tags : [javascript]
keywords: []
description: 
---
{% include JB/setup %}

事情的起因是这样的最近在业务代码中发现下面这样的一行代码，我看了半天没搞明白是什么意思，不知道聪明的你能不能知道是什么意思呢？

    !~location.href.search('***')

如果你也不知道，并且也像我一样富有好奇心那么就和我一起来学习这篇文章吧。在本文中你将学到如下知识：

- 二进制数的表示
- js中的二进制数整数
- js中的位运算

## 二进制数
本文假设你知道计算机中用二进制数来存储，计算数字，并且熟悉二进制数的表示方法。

为了实现不同的目的，其实都是为了简化问题，二进制数在计算机中有不同的表示方法，如原码、反码、补码和移码等。

**注意：**本文问了简化运算，二进制数都是用一个字节——8个二进制位来简化说明

先来说说真值吧，我们表示自然数包括正数，负数和0，下面是1和-1的二进制表示，我们称为真值

    + 00000001 # +1
    - 00000001 # -1

8位二进制数能表示的真值范围是[-2^8, +2^8]。

由于计算机只能存储0和1，不能存储正负，所以用8个二进制位的最高位来表示符号，0表示正，1表示负，用后七位来表示真值的绝对值，这种表示方法称为原码表示法，简称原码，上面的1和-1的原码如下：

    0 0000001 # +1
    1 0000001 # -1

由于`10000000`的意思是-0，这个没有意义，所有这个数字被用来表示-128，所有负数就比整数多一个。

由于最高位被用来表示符号了，现在能表示的范围是[-(2^7), +(2^7-1)]，即[-128, +127]

反码是另一种表示数字的方法，其规则是整数的反码何其原码一样，负数的反码将其原码的符号位不变，其余各位按位取反

    0 0000001 # +1
    1 1111110 # -1

反码的表示范围是[-(2^7), +(2^7-1)]，即[-128, +127]

补码是另外一种表示方法，主要是为了简化运算，将减法变为加法而发明的数字表示法，其规则是整数的补码和原码一样，负数的补码是其反码末尾加1

    0 0000001 # +1
    1 1111111 # -1

快速计算负数补码的规则就是，由其原码低位向高位找到第一个1，1和其低位不变，1前面的高位按位取反即可，不知道聪明的你能不能想到原理。

8位补码表示的范围是[-(2^7), +(2^7-1)]，即[-128, +127]

## js中的二进制数整数
再来说说js中的二进制整数表示，

## 参考资料
- [Numbers in JavaScript](http://jser.it/blog/2014/07/07/numbers-in-javascript/)