---
title: 一行ruby代码新建并写入内容至文件
date: 2018-03-19 21:58:47
tags:
categories: Ruby
---

一行ruby 代码写入文件

```ruby
open('create-first-file.txt', 'w'){|f| f.write 'Ruby content'}
```

