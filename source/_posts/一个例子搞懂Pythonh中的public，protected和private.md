---
title: 一个例子搞懂Pythonh中的public，protected和private
date: 2017-12-19 23:27:15
tags: 
categories: Python
---

关于Python中的private，protected和public：
Python中方法属性是否私有取决于它的名字，以一个下划线开头的方法为protected，可以被该类以及它的子类所访问，已两个下划线开头的方法为private，只能被本类访问
如果想访问private方法或者成员变量，可以新建一个public方法然后访问，或者在私有函数名前加上下划线和类名"_ClassName__privateMetnod"这样来访问


```Python
关于Python中的private，protected和public：
Python中方法属性是否私有取决于它的名字，以一个下划线开头的方法为protected，可以被该类以及它的子类所访问，已两个下划线开头的方法为private，只能被本类访问
如果想访问private方法或者成员变量，可以新建一个public方法然后访问，或者在私有函数名前加上下划线和类名"_ClassName__privateMetnod"这样来访问
class Foo:
    __privateVar = "this is a private variable"
    def __init__(self):
        pass
    def public_mehod(self):
        print("this is a public method")
    def _protected_method(self):
        print("this is a protected method")
    def __private_method(self):
        print("this is a private method")
    def access_private(self):
        self.__private_method()
        print(self.__privateVar)
class SubFoo(Foo):
    pass
s = SubFoo()
s.public_mehod()
s._protected_method()
s.access_private()
f = Foo()
f._Foo__private_method
print(f._Foo__privateVar)
```
参考链接[Private, protected and public in Python](http://radek.io/2011/07/21/private-protected-and-public-in-Python/)

