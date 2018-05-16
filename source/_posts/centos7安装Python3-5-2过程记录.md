---
title: centos7安装Python3和pip3过程记录
date: 2018-05-15 22:45:49
tags: Linux
categories: Python
---

 1.安装python3之前需要先进行编译编译环境的安装（敲黑板！！！）

```
yum install zlib-devel bzip2-devel openssl-devel ncurese-devel
```

要先安装这个不然python安装不完整，会没有pip3

接下来下载编译安装python3.5.2

```
sudo mkdir /usr/local/python3 # 创建安装目录
wget --no-check-certificate https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tgz
# 注意：wget获取https的时候要加上：--no-check-certificate
tar -xzvf Python-3.5.2.tgz # 解压缩包
cd Python-3.5.2
sudo ./configure --prefix=/usr/local/python3 # 指定创建的目录
sudo make
sudo make install
```

创建 python3 的软链接：

```
sudo ln -s /usr/local/python3/bin/python3 /usr/bin/python3
```

这样就可以通过 python 命令使用 Python 2，python3 来使用 Python 3。

2. 关于pip3

编译安装python3.5.2时会默认安装pip3，所以此时只要创建pip3的软链接即可

```
sudo ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
```



此时可使用python3＆ pip3了

参考链接

[centos在python3环境下安装PIP的问题](https://www.zhihu.com/question/30279880/answers/created)

[CentOS 7 安装Python3、pip3](http://notes.ehlxr.top/2017/01/07/CentOS-7-%E5%AE%89%E8%A3%85-Python3%E3%80%81pip3/#2-1-yum-%E5%AE%89%E8%A3%85)