---
title: Python中参数*args和**args的含义
date: 2018-01-23 22:52:07
tags: args
categories: Python
---

*args代表参数是以元组的形式传入的

**args代表参数是以元组的形式传入的

以例子说明

```Python
def tupleArgs(*targs):
    print(targs)
    for i in targs:
        print(i)
tupleArgs('a','b','c')
```

输出是

```
('a', 'b', 'c')
a
b
c
```

关于**args

```Python
def kwArgs(**targs):
    print(targs)
    for i in targs:
        print(i)
kwArgs(q='a',w='b',e='c')
```

输出是

```
{'q': 'a', 'e': 'c', 'w': 'b'}
q
e
w
```

注意：*args 和 **args也可以不传递参数