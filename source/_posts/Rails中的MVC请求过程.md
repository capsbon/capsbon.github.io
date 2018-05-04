---
title: Rails中的MVC请求过程
date: 2018-03-12 23:49:18
tags: 
categories: Ruby
---

ruby on rails 请求过程
1.浏览器向/users发起一个请求
2.Rails的路由通过 /users 调用UsersController中的index方法
3.index方法中定义从用户模型中读取所有用户(User.all)
4.用户模型从数据库中读取所有用户
5.用户模型把所有用户组成的列表返回给控制器
6.控制器把受到的列表赋值给@users变量，然后传入index视图
7.视图使用模板引擎把页面渲染成html
8.控制器把html页面传递给浏览器

参考链接：
[ruby知识点](https://www.jianshu.com/p/ad0e9460ac14)