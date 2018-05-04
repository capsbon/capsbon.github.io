---
title: CentOs7离线安装Python3.5
date: 2018-03-12 23:47:04
tags:
categories: Python
---

1.安装python3.5
下载python包
https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tgz。

```
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

2.安装pip
下载地址
https://github.com/pypa/pip/archive/9.0.1.tar.gz

```
tar -zvxf 9.0.1 -C pip-9.0.1    # 解压文件
cd pip-9.0.1
```

使用 Python 3 安装

```
python3 setup.py install
```

创建链接：

```
sudo ln -s /usr/local/python3/bin/pip /usr/bin/pip3
```

参考链接
[Python3.5安装](http://notes.ehlxr.top/2017/01/07/CentOS-7-%E5%AE%89%E8%A3%85-Python3%E3%80%81pip3/#2-1-yum-%E5%AE%89%E8%A3%85)