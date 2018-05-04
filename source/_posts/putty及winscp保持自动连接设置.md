---
title: putty及winscp保持自动连接设置
date: 2018-03-06 21:16:59
tags: Linux
categories: 
---

putty以及winscp一段时间不与服务器通信就自动断开连接，比较麻烦，

下面就介绍下如何保持putty以及winscp自动连接

1.putty:

打开putty,进去到命令行页面，在空白处右击选择Change Settings:

打开putty,"Connection"，改右边的"Seconds between keepaliaves(0 to turn off)"，默认是0，单位是秒，一般写10。意思是每隔10秒就给服务器发送一个空数据包，以免服务器长时间没有收到数据包而自动断开 ssh 连接。

修改完后需要保存到Session中，点击Session,在Saved Sessions下面框框下输入你想要保存的名字，

然后点击Save,最后Apply就大功告成了。

2.WinScp:

选项 -》选项 -》面板 -》远程，勾选刷新原创面板间隔(E)

后面的时间默认是60秒







