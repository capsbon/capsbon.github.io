---
title: 'mysql出现innodb:Cannot allocate memory for the buffer pool的解决办法'
date: 2018-03-04 23:10:48
tags: 
categories: DataBase
---
最近在做一个私人的Django项目，做完后打算放在自己的服务器上跑下，刚开始都
没什么问题，后来又想学习下docker,于是又在这台服务器上装了docker,然后就发现

Django跑不通了，提示是MySql数据库挂了。

想打开数据库看下

mysql -u fnst -p

输入密码后出现错误

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (111)

查看mysql日志

tail -30 /var/log/mysqld.log

出现

InnoDB: Cannot allocate memory for the buffer pool

错误

明显是内存不够用了

解决办法：

1.增大物理内存(呵呵，贵啊，不考虑)

2.更改/etc/my.cnf设置文件，减小innode_buffer_pool_size内存

vi /etc/my.cnf后发现

innode_buffer_pool_size默认设置128M(我的机器只有512M内存)

将其设置成64M

service mysqld restart

重启mysql后恢复正常

参考链接：

http://www.webtrafficexchange.com/solved-mysql-crash-fatal-error-cannot-allocate-memory-buffer-pool