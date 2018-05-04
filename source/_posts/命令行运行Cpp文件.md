---
title: 命令行运行Cpp文件
date: 2018-01-23 22:28:11
tags: 
categories: C++
---

本篇文章主要介绍如何在命令行下运行cpp文件，当然前提是你安装了vs2017。下面的步骤是在win10系统下进行的

1.打开VS 2017的开发人员命令提示符 

首先点击桌面最左下角，进入程序列表找到

在Visiual Studio2017文件夹下

找到   VS 2017的开发人员命令提示符  并打开

2.新建一个文件夹

在VS 2017的开发人员命令提示符 打开的窗口下输入

md hello

cd hello

此时在hello目录下

3.写代码

notepad hello.cpp

会提示你找不到文件：hello.cpp。要创建新文件吗，回车就好。

然后在hello.cpp上输入以下内容

```c++
#include<iostream>
using namespace std;
int main(){
    cout<<"Hello, World!"<<endl;
    return 0;
}
```
后保存

4.运行hello.cpp

输入cl /EHsc hello.cpp

此时下面应该会显示以下内容

'''

用于 x86 的 Microsoft (R) C/C++ 优化编译器 19.11.25547 版
版权所有(C) Microsoft Corporation。保留所有权利。

hello.cpp
Microsoft (R) Incremental Linker Version 14.11.25547.0
Copyright (C) Microsoft Corporation.  All rights reserved.

/out:hello.exe
hello.obj

'''

再输入hello

就会出现激动人心的

Hello, World! 

了

