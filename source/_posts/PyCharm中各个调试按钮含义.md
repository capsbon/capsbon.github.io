---
title: PyCharm中各个调试按钮含义
date: 2018-03-28 23:56:09
tags: tools
categories: Python
---

Shift+F9 /小瓢虫按钮 开始调试项目

点击那个小瓢虫按钮 开始调试项目，调试窗口有如下按钮，含义如下

`Step Over / F8`  在当前函数中跳到下一行执行，遇到子函数时不会进入子函数内单步执行

`Step Into / F7` 单步执行，遇到子函数就进入并且继续单步执行

`Step Out / Shift+F8` 跳到执行完当前函数后的下一行

`Run to Cursor / Alt+F9` 执行到下一个断点

`Step Into My Code / Alt+Shift+F7` 进入自己编写的函数，不进入系统函数