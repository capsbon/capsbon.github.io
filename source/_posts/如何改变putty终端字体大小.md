---
title: 改变putty终端字体大小及设置自动登录用户名
date: 2018-03-06 20:24:48
tags: Linux
categories: 
---

1.改变putty终端字体大小

由于putty连接Linux终端后默认的字体太小，于是想修改下

无奈修改完重新打开依然是以前的默认字体，搜索了下原来需

要保存到session中，设置步骤如下：

打开putty,进去到命令行页面，在空白处右击选择Change Settings:

依次选择

Window ->Appearance -> Font settings -> Change

点击Change后即可修改字体大小，我修改为14

然后需要保存到Session中，否则下次打开putty后又是默认的字体

了，

点击Session,在Saved Sessions下面框框下输入你想要保存的名字，

然后点击Save,最后Apply就大功告成了。

2.putty设置自动登录用户名,

打开putty,进去到命令行页面，在空白处右击选择Change Settings:

"Connection"，"Data"，修改"Auto-login username"的值即可，这样就不用每次都输用户名了。