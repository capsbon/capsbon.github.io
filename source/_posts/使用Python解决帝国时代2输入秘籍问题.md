---
title: 使用Python解决帝国时代2输入秘籍问题
date: 2018-05-05 17:29:33
tags:
categories: 
---

##### 交代下背景：

最近赋闲在家，想起以前玩的帝国时代，于是手痒下来玩玩。本着娱乐上百度的原则我在百度软件中心下载了这款游戏，没想到安装完成后捆绑了毒霸，爱奇艺等流氓软件，另外还篡改了我的主页，自以为不怕流氓的我这回竟也被流氓了一把。

闲话少叙，我打开帝国2后本着虐杀对手的心态先在网上找了秘籍，不过没想到每次只能加1000金币，粮食什么的，对于不勤快的我自然无法忍受，于是想到了Python有没有什么库可以模拟鼠标键盘操作的，没想到还真给我找到了，那就是PyUserInput

##### 具体操作说明

当然首先要安装PyUserInput库了

不过直接安装会报 Could not find a version that satisfies the requirement pyHook (from PyUserInput) 这种错误，说明我们要安装pyhook和pywin32

解决办法：

1、安装pywin32，下载地址 https://github.com/mhammond/pywin32/releases

2、在这个上面下载pyhook进行安装https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyhook

根据自己的系统并安装

然后使用

```
pip install PyUserInput
```

就装好我们所需要的库了

接下来就是写代码了

先放下我写的吧，很简单

```python
import time
from pymouse import PyMouse
from pykeyboard import PyKeyboard
m = PyMouse()
k = PyKeyboard()
time.sleep(3)
# 获取要点击软件的位置
po = m.position()
# print(type(po))
# m.click(415,711)
# 模拟鼠标点击
m.click(po[0], po[1])
time.sleep(2)
for i in range(20):
    # 按下回车键
    k.tap_key(k.enter_key,n=1,interval=1)
    # 输入ROCK ON
    k.type_string('ROCK ON')
    # 再按下回车键
    k.tap_key(k.enter_key,n=1,interval=1)

    k.tap_key(k.enter_key,n=1,interval=1)
    k.type_string('ROBIN HOOD')
    k.tap_key(k.enter_key,n=1,interval=1)

    k.tap_key(k.enter_key,n=1,interval=1)
    k.type_string('LUMBERJACK')
    k.tap_key(k.enter_key,n=1,interval=1)

    k.tap_key(k.enter_key,n=1,interval=1)
    k.type_string("CHEESE STEAK JIMMY'S")
    k.tap_key(k.enter_key,n=1,interval=1)

```

运行后把鼠标放到任务栏的帝国时代程序那就可以了，可以去喝杯茶，到外面休息休息。回来后你就会发现粮食金币全都加了20000了，好了，现在可以愉快地玩耍了。

参考链接：

[Win10 Python3.5 安装 pyuserinput报错坑](https://blog.csdn.net/zhusongziye/article/details/79241410)

[python3.5 &PyUserInput模拟鼠标和键盘模拟](https://blog.csdn.net/shij19/article/details/53046048)

[学习使用PyUserInput并用Python模拟鼠标的拖动](https://blog.csdn.net/frankfrankflb/article/details/79003423)
