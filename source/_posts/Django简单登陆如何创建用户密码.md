---
title: Django简单登陆如何创建用户密码
date: 2018-03-04 23:42:47
tags: Django
categories: Python
---

由于项目要求实现一个简单的登陆页面，然后搜索得知Django本身就有一些验证登陆的

类，于是去看官方文档，如下：

### Creating users[¶](https://docs.djangoproject.com/en/2.0/topics/auth/default/#creating-users)

The most direct way to create users is to use the included [`create_user()`](https://docs.djangoproject.com/en/2.0/ref/contrib/auth/#django.contrib.auth.models.UserManager.create_user) helper function:

```
>>> from django.contrib.auth.models import User
>>> user = User.objects.create_user('john', 'lennon@thebeatles.com', 'johnpassword')
# At this point, user is a User object that has already been saved
# to the database. You can continue to change its attributes
# if you want to change other fields.
>>> user.last_name = 'Lennon'
>>> user.save()
```

打开python交互页面，输入

from django.contrib.auth.models import User

user = User.objects.create_user('john', 'lennon@thebeatles.com', 'johnpassword')

不对，出错，App not registered之类的错误，

可能不是Python交互页面，搜了一堆文章就是没有说是在什么情况下输入上面两行代码来创建

用户，皇天不负有心人，终于让我找到了。

需要输入

python manage.py shell 

进入django的终端:

然后输入

from django.contrib.auth.models import User

user = User.objects.create_user('john', 'lennon@thebeatles.com', 'johnpassword')

来创建用户，接下来可以看我github里关于Danjo的小项目，里面有关于登陆页面的

简单实现：

https://github.com/capsbon/django_xml

