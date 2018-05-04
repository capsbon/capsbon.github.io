---
title: CentOs7离线安装MySql
date: 2018-03-12 23:46:05
tags:
categories: 数据库
---

1.下载安装mysql
下载安装包及其他依赖包：
mysql安装包
下载地址：http://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.18-1.el7.x86_64.rpm-bundle.tar
解压：
tar -zxf mysql-5.7.16-1.el7.x86_64.rpm-bundle.tar
得到包含以下文件的文件夹
mysql-community-client-5.7.18-1.el7.x86_64.rpm
mysql-community-common-5.7.18-1.el7.x86_64.rpm
mysql-community-libs-5.7.18-1.el7.x86_64.rpm
mysql-community-server-5.7.18-1.el7.x86_64.rpm

依赖包：
numactl 软件包：
numactl-2.0.9-4.el7_2.x86_64.rpm
numactl-devel-2.0.9-4.el7_2.x86_64.rpm
numactl-libs-2.0.9-4.el7_2.x86_64.rpm
其他相关支持：
perl-Data-Dumper-2.145-3.el7.x86_64.rpm
libaio-0.3.109-12.el7.x86_64.rpm

2.查询并卸载系统自带的Mariadb
在CentOS 7上已经有一个mariadb 而这个会与 MySQL的mariadb发生冲突。
所以需要将系统自带的mariadb卸载掉，然后使用mysql自带的mariadb。

```
rpm -qa | grep mariadb

rpm -e --nodeps mariadb-libs-5.5.37-1.el7_0.x86_64 
```

其中mariadb-libs-5.5.37-1.el7_0.x86_64 是我刚刚用rpm -qa | grep mariadb查询出的结果。不同版本可能会有所不同。

3.安装提供的依赖包

安装 libaio-0.3.109-13.el7.x86_64.rpm
$ rpm -ivh libaio-0.3.109-13.el7.x86_64.rpm

安装numactl相关
$rpm -ivh numactl* 

安装perl相关
$rpm -ivh --nodeps perl-5.16.3-285.el7.x86_64.rpm
$rpm -ivh --nodeps perl-Getopt-Long-2.40-2.el7.noarch.rpm
$rpm -ivh --nodeps perl-Data-Dumper-2.145-3.el7.x86_64.rpm
$rpm -ivh --nodeps perl-DBD-MySQL-4.023-5.el7.x86_64.rpm

安装mysql
$rpm -ivh mysql-community-*

4.启动mysql服务

```
systemctl start mysqld
```

5.设置开机启动

```
systemctl enable mysqld

systemctl daemon-reload
```

6.修改mysql root 密码

cat /var/log/mysqld.log | grep password
查询结果为临时密码

[root@localhost ~]# mysql -u root -p

Enter password:

输入临时密码 进入mysql命令行；

设置root新密码newpass

```
SET PASSWORD FOR ‘root’@’localhost’ = PASSWORD(‘newpass’);
```

7.创建新用户并开启远程登陆

创建远程访问用户user02

```
create user user02@’%’ identified by ‘password’;
```


授予user01管理dbdata的全部权限

```
grant all privileges on dbdata.* to user02;
```

开启3306端口

```
[root@localhost ~]#firewall-cmd --zone=public --add-port=3306/tcp --permanent
```

注意：在centos 7中，默认的防火墙由iptables改为Firewall，默认是没有安装iptables的，并且Firewall默认是启动状态。

```
[root@localhost ~]#firewall-cmd –reload
```

8.配置默认编码为UTF-8

修改/etc/my.cnf配置文件，在[mysqld]下添加编码配置，如下所示：

```
[mysqld]

character_set_server=utf8

init_connect=’SET NAMES utf8’
```

编辑保存完 重启mysql服务；

```
[root@localhost ~]# systemctl restart mysqld
```

