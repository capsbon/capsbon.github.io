---
title: systemctl中的ctl代表含义
date: 2018-03-12 23:41:18
tags: Linux
categories: 
---

systemctl命令是Linux系统服务管理器指令，它实际上将 service 和 chkconfig 这两个命令组合到一起

举例子，开启MySql服务

```
systemctl start mysqld #以前是service mysqld start
```

官方说明：

systemctl — Control the systemd system and service manager

以前一直想systemctl中的ctl 什么意思，后来谷歌了下，发现是Control的意思啊

还有 ps aux |grep python 中的ps代表 process status

常见缩写i18n、addr、msg、btn等

