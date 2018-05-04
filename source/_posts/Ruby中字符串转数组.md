---
title: Ruby中字符串转数组和数组去重
date: 2018-01-23 23:27:09
tags: 
categories: Ruby
---

以字符串"games,fun,sports"为例

1.可以使用split(',')转化成数组
"games,fun,sports".split(',') # => ["games", "fun", "sports"]

2.如果是JSON格式的字符串，例如'["games", "fun", "sports"]'

'["games", "fun", "sports"]'.split(',')  # =>  ["[\"games\"", " \"fun\"", " \"sports\"]"]

 不是我们想要的结果,此时可以使用json库来格式化字符串,此时可以

require 'json'
JSON['["games", "fun", "sports"]'] # => ["games", "fun", "sports"]

即可
原文是来自stackoverflow的问题
原文链接https://stackoverflow.com/questions/39337794/how-to-convert-a-string-to-an-array-using-Ruby-on-rails



数组去重可以：

array = array.uniq
uniq 方法删除所有重复的元素，并保留数组中的所有唯一元素。