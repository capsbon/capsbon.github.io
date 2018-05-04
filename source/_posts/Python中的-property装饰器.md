---
title: Python中的@property装饰器
date: 2018-01-29 21:57:15
tags: Decorator
categories: Python
---

Python中的@property
使用@property可以使我们的函数像属性一样被使用，具体使用方法：

```Python
class Grades:
    @property
    def score(self):
        return self.scoreValue

    @score.setter
    def score(self,value):
        if not isinstance(value, int):
            raise ValueError('Input must be a Integer')
        if value<0 or value>100:
            raise ValueError('Input must between 1~100')
        self.scoreValue = value
        
g = Grades()

g.score = 7

print(g.score)
#output => 7
```


可以看出，我们可以像使用属性一样来使用函数，不过注意scoreValue不能写成score，除此之外的都可以，
推荐写成私有变量  _score 的形式，这里为了便于理解只写成了scoreValue

那为什么我们要使用它以及什么时候应该使用它呢
请看官方解释https://www.programiz.com/Python-programming/property的
译文在这http://Python.jobbole.com/81967/