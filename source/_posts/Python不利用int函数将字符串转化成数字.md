---
title: Python不利用int函数将字符串转化成数字
date: 2018-05-16 22:36:20
tags:
categories: Python
---

之前虽然做过这样的题目不过是直接用int函数转化的，既然要求不用int函数，现在再解答下吧

题目：将字符串'1234'转化成数字1234

思路：不让用int(),不过没有限制用str(),只要将字符串每个字符单独抽出来和0-9的数字比较即可，再根据所处的位置确定位数，代码如下

```python
# '1234' => 1234


def transfer_int(string_a):
    str_len = len(string_a)
    result = 0
    for i in range(str_len):
        int_a = single_int(string_a[i])
        #根据所处的位置确定位数
        result = result + int_a*(10**(str_len-i-1))
    print(result)

# 将单个字符转化为int型
def single_int(char_a):
    for i in range(10):
        if str(i) == char_a:
            return i
        
        
transfer_int('1234')

```

其中single_int方法也可以使用ord函数实现，代码如下

```
def single_int(char_a):
    rlt = ord(char_a) - ord('0')
    return rlt
```

- ord() 函数是 chr() 函数（对于8位的ASCII字符串）或 unichr() 函数（对于Unicode对象）的配对函数，它以一个字符（长度为1的字符串）作为参数，返回对应的 ASCII 数值，或者 Unicode 数值


- chr() 用一个范围在 range（256）内的（就是0～255）整数作参数，返回一个对应的字符