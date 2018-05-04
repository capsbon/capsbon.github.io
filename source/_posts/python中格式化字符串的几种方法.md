---
title: python中格式化字符串的几种方法
date: 2018-03-05 00:11:36
tags:
categories: Python
---
平时写代码难免要与字符打交道，格式化字符串又是我们经常遇到的

问题，下面我就稍微整理以下常用的方法吧

1. 使用%s格式化字符串

   举个例子

   1.传递单个参数

   name = 'tom'
   print("I'm %s." %name)

   \# output => I'm tom

   2.需要传递多个参数时使用元组：

   name = 'tom'

   age = 10

​       print("I'm %s. I'm %d year old" % (name,age))

​        \# output => I'm tom. I'm 10 year old

2. format格式化字符串

   str.format()可以通过位置，关键字参数和下标来格式化字符串

   1.通过 位置
   In [1]: '{0},{1}'.format('kzc',18) 
   Out[1]: 'kzc,18'
   2.通过关键字参数
   In [5]: '{name},{age}'.format(age=18,name='kzc') 
   Out[5]: 'kzc,18'

   3.通过下标

   In [5]: print("{1[0]} is {1[1]} years old".format(["wang",21],["li",18]))

   Out[5]: li is 18 years old