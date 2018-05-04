---
title: 几个例子搞懂Python类里的self和__init__
date: 2017-12-19 23:12:06
tags: 
categories: Python
---
Python中的self和\_\_init\_\_都是在类中使用的

那么我们为什么要使用类呢？举个例子，让我们回到人类诞生前，现在你是女娲，
想仿造自己造几个生物，造了几个之后发现他们看起来都差不多，于是把他们都归类为人这个物种。
这时候我们可以把人看做一个类，其中女娲造的几个‘人’分别叫小红，小明，小华，他们三个分别都是‘人‘这个类的实例，
人刚生下来总要哭几声，这相当于类的初始化方法，也就是\_\_init\_\_的由来
让我们动手敲下吧，首先定义一个Python类class BaseClass:

```Python
class BaseClass:
    def __init__(self,name,age):
        self.name = name
        self.age = age
        print("BaseClass is inited")
    def speak(self,name):
        print('%s is speaking'%name)
if __name__ == '__main__':
    b = BaseClass('jim',16)   # 输出 BaseClass is inited
    b.speak('tom')            # 输出 tom is speaking
```
如果没有手动创建\_\_init\_\_方法，，则Python会自动生成一个\_\_init_\_方法，不过它什么也不干class BaseClass:

```Python
class BaseClass:
    # def __init__(self,name,age):
    #     self.name = name
    #     self.age = age
    #     print(self.name)
    #     print("BaseClass is inited "+self.name)
    def speak(self,name):
        print('%s is speaking'%name)
if __name__ == '__main__':
    b = BaseClass()
    # b.speak('tom')
    print(b.__init__)
```
不过要注意创建实例的时候传入参数要和\_\_init_\_方法接受的参数一致。

关于Python的继承，在子类没有定义__init__方法时，会调用父类的__init__方法，其他方法同理。
如果子类有定义的话会执行子类的方法，不执行父类中的方法。

```Python
class BaseClass:
    def __init__(self,name,age):
        self.name = name
        self.age = age
        print("BaseClass is inited ")
    def speak(self,name):
        print('%s is speaking'%name)
class SubClass(BaseClass):
    def __init__(self):
        print('SubClass is inited')
    # def speak(self,name,age):
    #     print('name is %s,age is %s'%(name,age))
if __name__ == '__main__':
    a = SubClass()
    a.speak('baby')
```


关于Python中的self，指的是当前类的实例。比如在b = BaseClass()此时的self 就代表 b
从下面可以看出

```Python
class BaseClass:
    def __init__(self):
        print(self)
if __name__ == '__main__':
    b = BaseClass()
    print(b)
    a = BaseClass()
    print(a)
```


输出
<__main__.BaseClass object at 0x00000000006E6B70>
<__main__.BaseClass object at 0x00000000006E6B70>
<__main__.BaseClass object at 0x0000000000ACBB38>
<__main__.BaseClass object at 0x0000000000ACBB38>
为什么要有self呢，向其他语言比如Ruby，就没有
这应该和Python的设计哲学有关吧
*Explicit is better than implicit*
显式比隐式更好