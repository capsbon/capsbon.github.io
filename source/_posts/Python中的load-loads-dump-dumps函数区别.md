---
title: 'Python中的load,loads,dump,dumps函数区别'
date: 2018-03-05 00:32:53
tags:
categories: Python
---
实例如下：
\# Writing JSON data 将data写入到data.json文件中
```python
with open('data.json', 'w') as f:
    json.dump(data, f)
```
\# Reading data back 将data.json中数据取出放到data.json里
```python
with open('data.json', 'r') as f:
    data = json.load(f)
```

简单来说：

python中loads()和load()的区别
loads()操作的是字符串，将str转化成字典
load()的操作与文件有关
dumps()操作的是字典，将字典转化成str
dump()操作也是与文件有关