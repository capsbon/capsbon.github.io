---
title: Python中如何获取随机数
date: 2018-03-05 00:30:41
tags:
categories: Python
---

python获取随机数
import random

\#获取0到1之间的随机小数
random.random()
\#获取指定范围a到b之间的随机小数
random.uniform(a,b)
\#获取指定范围a到b之间的随机整数,包含a,b
random.randint(a,b)
\#随机获取列表里的一个值
random.choice(list_a)