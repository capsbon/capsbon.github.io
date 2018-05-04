---
title: 使用Python批量替换多个文件中的字符
date: 2018-03-02 00:08:22
tags:
categories: Python
---

先交代下背景：

说起来有点惭愧，之前博客中'Python'中的'P'全部是小写的，最近意识到这样是不对的，因此想要将博客里的'python'全部改为'Python',不过写了也有大概五十篇左右的博客，而且每篇博客里的'python'可能还不止一处，遂放弃手动修改的想法，打算写个小程序批量修改。

代码如下

```python
#!/usr/bin/python3
# -*- coding:utf8 -*-
import os
import re
import chardet
# 获取文件编码类型
def get_encoding(file):
    # 二进制方式读取，获取字节数据，检测类型
    with open(file, 'rb') as f:
        return chardet.detect(f.read())['encoding']
base_dir = r"C:\capsbon.github.io\source\_posts"
os.chdir(base_dir)
mulu = os.listdir(base_dir)
for md_file in mulu:
    #print(md_file)
    encoding_type = get_encoding(md_file)
    #指定编码方式
    f = open(md_file,'r',encoding=encoding_type)
    lines = f.read()
    f.close()
    f = open(md_file,'w+',encoding=encoding_type)
    #将'python'替换成'Python'
    newline = re.sub('python','Python',lines)
    f.write(newline)
    f.close()
```

需要注意的是编码问题，因为有的文件编码方式是'gb2312',有的是'UTF-8'.在读取文件（f.read()）时会出现"UnicodeDecodeError: 'utf-8' codec can't decode byte 0xd6 in position 16"这种错误，因此我的想法时每次读取时指定编码方式，因此定义get_encoding()方法来获取文件编码方式，感觉这个方法可能较笨，如果读者有更好的方法，麻烦告知，不胜感激，可以在下面评论或者发邮件给我。