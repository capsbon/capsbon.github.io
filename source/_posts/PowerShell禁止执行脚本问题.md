---
title: PowerShell禁止执行脚本问题
date: 2018-03-19 21:36:17
tags:
categories: tools
---

Win10 PowerShell因为在此系统中禁止执行脚本 
解决方法:
打开PowerShell(管理员)
键入

```
set-executionpolicy remotesigned
```


出现以下信息

```
执行策略可以防止您执行不信任的脚本。更改执行策略可能会使您面临 about_Execution_Policies 
帮助主题中所述的安全风险。
是否要更改执行策略? [Y] 是(Y) [N] 否(N) [S] 挂起(S) [?] 帮助 (默认值为“Y”): y
```

输入 y 即可