---
title: Python中is和==的区别
date: 2018-02-27 21:25:11
tags:
categories: Python
---

Python中万物皆对象。

每个对象包含三个属性，分别是id(内存地址)；type(类型)；value(值)

is就是比较id是否相等

==就是比较value是否相等

不过要注意的是Python为了实现对内存的有效利用，对小整数[-5,256]内的整数会进行缓存，不在该范围内的则不会缓存，具体如下

\>>> a = 255

\>>> b = 255

\>>> a is b

True

\>>> c = 257

\>>> d = 257

\>>> c is d

False

\>>>

可见a,b的id是相同的，而c和d的id是不同的

