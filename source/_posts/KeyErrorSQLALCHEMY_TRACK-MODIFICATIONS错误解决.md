---
title: KeyErrorSQLALCHEMY_TRACK_MODIFICATIONS错误解决
date: 2018-03-13 00:39:00
tags:
categories: Python
---

运行flask项目中出现

 SQLAlchemy：KeyError：'SQLALCHEMY_TRACK_MODIFICATIONS'错误

原因：在代码中有两个app = Flask(__name__)可能会导致此问题。 

删掉其中一个换成导入形式的即可