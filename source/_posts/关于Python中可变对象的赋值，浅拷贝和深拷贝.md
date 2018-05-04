---
title: 关于Python中可变对象的赋值，浅拷贝和深拷贝
date: 2018-01-29 21:09:59
tags: 
categories: Python
---
关于可变对象的赋值，浅拷贝和深拷贝
Python中list ,dict为可变对象，int,string,float,tuple为不可变对象

1.赋值
list_b = list_a
修改list_a的同时list_b也会发生改变

\>>> list_a = [2,3]
\>>> list_b = list_a
\>>> list_a.append(5)
\>>> list_a
\>>> [2, 3, 5]
\>>> list_b
\>>> [2, 3, 5]
\>>>

2.使用浅拷贝的话list_b就不会发生改变（在自身内部没有可变情况的情况下）
使用浅拷贝
list_b = list_a.copy()或者
import copy
list_b = copy.copy(list_a)

3.若list_a内有可变对象元素的话，若此时这个可变元素对象发生改变，则浅拷贝的list_b
也会变化，
此时我们可以采用深拷贝来避免这种情况
import copy
list_b = copy.deepcopy(list_a)