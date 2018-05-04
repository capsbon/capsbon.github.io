---
title: AppRegistryNotReady错误解决办法
date: 2018-03-05 00:03:45
tags: Django
categories: 
---

问题背景：

这是我在单独运行Django中某文件导入库时出现的问题

导入models.py里的库

```
from vacancy.models import Vacancies
```

运行该文件（此处为parse_data.py时就会出现以下错误）

django.core.exceptions.AppRegistryNotReady: Models aren't loaded yet.

解决办法：

在该文件（此处为parse_data.py）最上方加上以下代码

import os,django

os.environ.setdefault("DJANGO_SETTINGS_MODULE", "mysite.settings")
django.setup()

即可