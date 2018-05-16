---
title: Linux下如何导出MySQL数据库
date: 2018-03-04 23:57:49
tags: Linux
categories: DataBase
---

命令行下执行

mysqldump -u userName -p  dabaseName  > fileName.sql

其中fileName.sql最好加上路径名,不加则导出到当前目录