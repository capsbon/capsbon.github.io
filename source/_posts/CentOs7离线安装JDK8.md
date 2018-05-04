---
title: CentOs7离线安装JDK8
date: 2018-03-12 23:46:48
tags: Linux
categories: 
---

1
下载jdk8安装包
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
上传到linux服务器后执行

```
tar -xvf jdk-8u161-linux-x64.tar.gz -C /usr/local
```

解压到当前目录,此时目录/usr/java
2.
添加到环境变量

```
vi /etc/profile
```

在export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE HISTCONTROL下面添加如下代码：

```
export JAVA_HOME=/usr/local/jdk1.8.0_111
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

3.
使配置生效

```
source /etc/profile
```

4.

查看安装是否成功

```
java -version
```

