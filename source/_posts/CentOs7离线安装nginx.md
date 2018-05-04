---
title: CentOs7离线安装nginx
date: 2018-03-12 23:46:21
tags: Linux
categories: 
---

说明，以下的包可以谷歌得到，或者通过打开CentOs系统安装包.iso文件中的packages文件夹中找到

1.安装gcc,提供如下的包

```
cpp-4.8.3-9.el7.x86_64.rpm
gcc-4.8.3-9.el7.x86_64.rpm
glibc-devel-2.17-78.el7.x86_64.rpm
glibc-headers-2.17-78.el7.x86_64.rpm
kernel-headers-3.10.0-229.el7.x86_64.rpm
libmpc-1.0.1-3.el7.x86_64.rpm
mpfr-3.1.1-4.el7.x86_64.rpm
```

统一安装命令

```
rpm -Uvh *.rpm --nodeps --force
```

验证是否安装成功

```
gcc -v
```

2.安装pcre

```
rpm -ivh pcre-8.32-14.el7.x86_64.rpm
rpm -ivh pcre-devel-8.32-14.el7.x86_64.rpm
```

3.安装libstdc++-devel（gcc-c++依赖）

```
rpm -ivh libstdc++-devel-4.8.3-9.el7.x86_64.rpm
```

4.安装gcc-c++

```
rpm -ivh gcc-c++-4.8.3-9.el7.x86_64.rpm
```

5.安装zlib-devel

```
rpm -ivh zlib-devel-1.2.7-13.el7.x86_64.rpm
```

6.下载安装nginx

下载地址：[nginx-1.13.7.tar.gz](http://nginx.org/download/)

```
tar -zxvf nginx-1.13.7.tar.gz

cd nginx-1.13.7

./configure

make

make install
```

7.测试是否安装成功
启动nginx

```
/usr/sbin/nginx
```

用ps aux来查看nginx是否启动

```
ps aux|grep nginx
```

8.配置开机启动

```
systemctl enable nginx.service
```

