---
title: Ruby中的attr_accessor是什么
date: 2018-03-19 21:01:04
tags:
categories: Ruby
---

﻿ruby中attr_accessor的作用

假设我们新建了一个类Person

```ruby
class Person
end

person = Person.new
person.name # => 运行出错，NoMethodError
```

很明显我们没有定义name方法，接下来定义name方法

```ruby
class Person
  def name
    @name # simply returning an instance variable @name
  end
end

person = Person.new
person.name # => nil
person.name = "Dennis" # => no method error
```

此时我们可以读取name的值，但是不能给name赋值，这是两个不同的方法前一个被称为reader后一个被称为writer，上面出错的原因是我们没有创建writer,接下来就来创建它吧

```ruby
class Person
  def name
    @name
  end

  def name=(str)
    @name = str
  end
end

person = Person.new
person.name = 'Dennis'
person.name # => "Dennis"
```

非常棒，现在我们使用reader和writer方法既可以读取实例变量@name也可以给它赋值了。不过，这样的操作是非常频繁的，为什么我们每次都要浪费时间来写这些函数呢，我们可以更以更简单的方式实现它

```ruby
class Person
  attr_reader :name
  attr_writer :name
end
```

这样看起来好像也有点重复，当你需要reader和writer时只需要使用accessor就可以了

```ruby
class Person
  attr_accessor :name
end

person = Person.new
person.name = "Dennis"
person.name # => "Dennis"
```

同样生效了，猜测:此时person类中的实例变量@name就像我们手动创建它一样，你可以在其他方法中使用它

```ruby
class Person
  attr_accessor :name

  def greeting
    "Hello #{@name}"
  end
end

person = Person.new
person.name = "Dennis"
person.greeting # => "Hello Dennis"
```

就是这样了，为了理解attr_reader, attr_writer,attr_accessor是如何生成方法的，请阅读其他答案，书，还有ruby的官方文档
原文链接：[What is attr_accessor in Ruby?](https://stackoverflow.com/questions/4370960/what-is-attr-accessor-in-ruby)