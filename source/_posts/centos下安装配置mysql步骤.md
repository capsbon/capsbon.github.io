---
title: centos下安装配置MySQL步骤
date: 2018-01-27 17:13:28
tags: 
- MySQL
- Linux
categories: DataBase
---

1.下载安装mysql源

下载：

```
wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
```

安装：

```
yum -y localinstall mysql57-community-release-el7-11.noarch.rpm
```

2.在线安装Mysql

```
yum -y install mysql-server
```

3.启动mysql服务

```
systemctl start mysqld
```

4.设置开机启动

```
systemctl enable mysqld
systemctl daemon-reload
```

5.修改mysql root 密码

```
cat /var/log/mysqld.log | grep password
```

在其中找到A temporary password is generated for root@localhost: 

后面那一串就是密码

```
mysql -u root -p
```

Enter password:

输入临时密码 进入mysql命令行；

设置root新密码newpass

```
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpass');
```

6.创建新用户并开启远程登陆

创建远程访问用户user02

```
create user user02@'%' identified by 'password';
```


授予user01管理dbdata的全部权限

```
grant all privileges on dbdata.* to user02;
```

开启3306端口

```
firewall-cmd --zone=public --add-port=3306/tcp --permanent
```

注意：在centos 7中，默认的防火墙由*iptables*改为*Firewall*，默认是没有安装*iptables*的，并且*Firewall*默认是启动状态。

```
firewall-cmd --reload
```

7.配置默认编码为utf-8

修改/etc/my.cnf配置文件，在[mysqld]下添加编码配置，如下所示：

```
[mysqld]
character_set_server=utf8
init_connect='SET NAMES utf8'
```

编辑保存完 重启mysql服务；

```
systemctl restart mysqld
```



参考链接 [centOS之MySQL安装](http://blog.csdn.net/Afox4l/article/details/79059473)