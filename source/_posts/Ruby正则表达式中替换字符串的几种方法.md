---
title: Ruby正则表达式中替换字符串的几种方法
date: 2018-03-25 21:41:56
tags: regex
categories: Ruby
---

Ruby正则表达式替换字符串有sub,sub!,gsub,gsub!几种方法，下面介绍下它们的区别

首先是sub()+gsub()的区别
sub只替换第一次匹配，gsub（g:global）会替换所有的匹配，没有匹配到返回原字符串的copy

```
str = "ABDADA"

new_str = str.sub(/A/, "") 	#返回"BDADA"

new_str2 = str.gsub(/A/, "")	#返回"BDD"
```


如果想修改原始字符串用sub!()和gsub!()，没有匹配到返回nil。

```
irb(main):077:0> str = "ABDADA"

=> "ABDADA"

irb(main):078:0> str.sub!(/A/, "*")

=> "*BDADA"

irb(main):079:0> str

=> "*BDADA"
```
