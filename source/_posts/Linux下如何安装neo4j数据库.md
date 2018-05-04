---
title: Linux下如何安装neo4j数据库
date: 2018-01-16 23:35:20
tags: NEO4J
categories: 数据库
---
运行neo4j前需要先安装JDK8

----------

#### 安装jdk8

1.获取jdk8安装包，上传到linux服务器后执行
tar -xvf jdk-8u5-linux-x64.tar.gz
解压到当前目录,此时目录/usr/java

2.添加到环境变量
vi /etc/profile
在export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE HISTCONTROL下面新增三行：
export JAVA_HOME=/usr/local/jdk1.8.0_111
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

3.使配置生效
source /etc/profile

#### 安装NEO4J

1.获取neo4j
访问https://neo4j.com/download/other-releases/找到对应的neo4j的版本下载
此次安装版本是 neo4j-community-3.3.1-unix.tar.gz

2.解压
tar -zxvf neo4j-community-3.3.1-unix.tar.gz
此时路径为/usr/java

3.开启远程访问
vi /usr/java/neo4j-community-3.3.1/conf/neo4j.conf
将 #dbms.connectors.default_listen_address=0.0.0.0 注释去掉
改为 dbms.connectors.default_listen_address=0.0.0.0

4.开放端口
iptables -I INPUT -p tcp --dport 7474 -j ACCEPT

5.添加环境变量
vi /root/.bash_profile
新增一行
export PATH=/usr/java/neo4j-community-3.3.1/bin:$PATH
保存后执行
source .bash_profile

6.设置操作系统文件句柄
打开设置操作文件系统文件句柄，Neo4j默认使用的最小文件句柄是40000，
而Linux操作系统一般默认是1024。
vi /etc/security/limits.conf
在其中增加两行
neo4j  soft   nofile  40000
neo4j  hard   nofile  40000


7.启动neo4j
neo4j start

查看neo4j状态
neo4j status

停止运行neo4j
neo4j stop