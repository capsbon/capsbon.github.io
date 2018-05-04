---
title: 关于Ruby的一些知识
date: 2017-09-10 13:15:21
tags: 
categories: Ruby
---

### 1.对于mix-in理解：

Ruby语言在设计时没有使用类似C++的多重继承，而是采用单继承的方式，
所以使用mix-in来解决Ruby中多重继承的问题，比如说可以为一个类可以增加功能，
而不用设计多层继承关系


### 2.对于Assets Pipline理解：
是一个用来处理JavaScript和CSS的框架，比如说合并js文件，合并压缩CSS文件，
可以减少http request的请求次数，能够加快网站的加载速度


### 3.Ruby中module和class的区别：
①class可以实例化，module不行
②class使用 "<" 作为继承的关键字，而module使用 "include
③模块可以混入(可以理解为minin)到对象中，达到类似多重继承的效果
