---
title: Python中的@staticmethod和@classmethod实例解析
date: 2017-12-19 23:32:29
tags: Decorator
categories: Python
---

Python中的装饰器@classmethod和@staticmethod：
一般来说，如果需要使用某个类的方法，需要先实例化再调用，而使用@staticmethod或@classmethod，就可以不需要实例化，直接类名.方法名()来调用。
@staticmethod不需要表示自身对象的self和自身类的cls参数，就跟使用函数一样。
@classmethod也不需要self参数，但第一个参数需要是表示自身类的cls参数
好处：以后重构类的时候不必要修改构造函数，只需要额外添加你要处理的函数，然后使用装饰符 @classmethod 就可以了
具体用法如下

```Python
class Foo:
    def __init__(self):
        print('init is called')
    def speak(self):
        print('speaking ')
    @staticmethod
    def static_method():
        print('this is a static method')
    @classmethod
    def class_method(cls):
        print('this is a class method')
Foo.static_method()
Foo.class_method()
#Foo.speak()
```
