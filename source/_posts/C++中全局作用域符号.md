---
title: 'C++中全局作用域符号::'
date: 2018-01-23 23:31:42
tags: 
categories: Cpp
---

c++ 中::可表示全局作用域符号

```c++
int i=10;
int main(){
	int i=20,j=7;
	cout<<i+::i%c;
	return 0;
}
```
输出结果是23