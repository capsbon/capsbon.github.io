---
title: Linux上安装Django的几种方法
date: 2018-03-06 22:55:42
tags: 
- Django
- Linux
categories: 
---

1.在线安装

```
pip install django
```

2.源码安装

Ⅰ.访问[django下载页面](https://www.djangoproject.com/download/)上下载tar.gz源码包：

输入以下命令并安装：

```
tar xzvf Django-X.Y.tar.gz    # 解压下载包
cd Django-X.Y                 # 进入 Django 目录
python setup.py install       # 执行安装命令
```

Ⅱ.github上下载zip源码

```
unzip django-master.zip -d saveDir      #linux上解压zip文件到saveDir文件夹

python setup.py install       # 执行安装命令
```

