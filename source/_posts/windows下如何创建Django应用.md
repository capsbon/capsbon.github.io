---
title: windows下如何创建Django应用
date: 2018-03-01 22:02:51
tags: Django
categories: Python
---

由于之前关于Python的Web框架只接触过flask,正好这次需要用到Django来完成项目，因此记录下使用过程，若有错误，希望不吝赐教。

1.安装Django

前提是机器上已经安装了Python和pip(啪，还用你说吗)

然后执行pip install django即可(需要科学上网环境，否则可能安装失败)

验证是否安装成功方法：

进入python环境后

\>>>import django
\>>>print(django.get_version())
2.0.2

正确输出了django的版本号，代表安装成功。

2.创建Django项目

为了保证不同项目之间依赖包不冲突，我们需要使用Python的虚拟环境，需要安装virtualenv

pip install virtualenv

执行

virtualenv venv

即创建了一个名为venv的文件夹(虚拟环境)

执行 venv\Scripts\activate 即可进入虚拟环境

接下来我们需要运行一些Django自带的脚本，它会生成一些文件夹及文件，在我们的项目中需要使用到它们。

(venv) E:\Maximum>django-admin startproject mysite .

注意不要忘记最后的小数点，它告诉脚本会将Django自动安装到当前目录中

此时我们的目录结构应该是这样的

```
Maximum
├───manage.py
└───venv
└───mysite
        settings.py
        urls.py
        wsgi.py
        __init__.py
```



`manage.py` 是一个帮助管理站点的脚本。在它的帮助下我们将能够在我们的计算机上启动一个 web 服务器，而无需安装任何东西。

`settings.py` 文件包含的您的网站的配置数据。

`urls.py` 文件包含该 Django 项目的 URL 声明; 一份由 Django 驱动的网站"目录"。

`__init__` 一个空文件，告诉 Python 该目录是一个 Python 包。

`wsgi.py` 一个 WSGI 兼容的 Web 服务器的入口，以便运行你的项目。

3.启动Django

进入到项目所在目录，命令行下执行

```
python manage.py runserver 0.0.0.0:8000
```

访问http://127.0.0.1:8000/

出现'The install worked successfully! Congratulations!'字样代表我们的Django项目已成功运行

好了，安装创建一个最简单的Django应用就到此结束了。