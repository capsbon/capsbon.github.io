---
title: Python计算斐波那契数列的两种方法
date: 2018-01-29 21:59:48
tags: Fibonacci 
categories: problems
---

计算斐波那契数列的两种方法，递归和迭代


```Python
def fib_recursion(n):
    assert n>=0, 'Parameter must be a positive integer'
    if n <= 1:
        return n
    else:
        return fib_recursion(n-1) + fib_recursion(n-2)
      
def fib_iteration(n):
    assert n>0, 'Parameter must be a positive integer'
    a,b=0,1
    for i in range(n):
        a,b =b,a+b
    return a

print(fib_iteration(10))
#output => 55
print(fib_recursion(10))
#output => 55
```

Python里assert用法

assert condition,  AssertionErrorString
举例
assert 2>5, '2 is less than 5'
执行的话就出错误信息就会包含'2 is less than 5'