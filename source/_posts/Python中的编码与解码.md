---
title: Python中的编码与解码
date: 2018-01-29 21:47:50
tags:
categories: Python
---

Python3中文本总是Unicode,由str类型进行表示;

二进制数据使用bytes进行表示

#####字符串通过编码成为字节码，字节码通过解码成为字符串。

str类型编码采用encode()方法编码
str.encode() 可以接受参数表明编码方式
str.encode('utf-8')

bytes类型采用decode()方法解码
bytes.decode()同样可以接受参数表明解码方式
bytes.decode('utf-8')
不加参数的话，默认采用utf-8编码和解码
官方文档
https://docs.Python.org/3/library/stdtypes.html?highlight=decode#str.encode
https://docs.Python.org/3/library/stdtypes.html?highlight=decode#bytes.decode



