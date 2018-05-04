---
title: 如何使用pry-byebug调试ruby程序
date: 2018-03-19 21:54:53
tags:
categories: Ruby
---

调试ruby on rails需要使用到pry-byebug包
在Gemfile文件中里添加

```
gem 'pry-byebug'
```

然后命令行下执行

```
bundle install
```

使用方法：
在需要调试的代码地方添加

```
binding.pry
```

实例

```ruby
def some_method
  puts 'Hello World' # Run 'step' in the console to move here
end

binding.pry
some_method          # 在此处停止
puts 'Goodbye World' # 命令行输入next执行下一步，也可在命令行输入想要查看的变量
```

参考官方文档

[pry-byebug](https://github.com/deivid-rodriguez/pry-byebug)