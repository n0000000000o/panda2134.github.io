---
layout: post
title: '单调数据结构学习笔记'
category: ["笔记"]
tags: ["单调栈","单调队列"]
comments: true
---

这里的“单调数据结构”，指的就是单调栈和单调队列

## 单调栈

###特点

FIFO，求前/后缀最值。

### 实现

维护一个栈，每次在加入栈时维护单调性。不断弹出栈顶元素，直到栈顶元素大于将要加入
的元素，此时再将要加入的元素推入栈中。具体地讲，由于需要随机访问单调栈中的元素，
以便充分利用其单调的特性，常用一个数组来模拟栈。
<!--more-->
设`s[0]`为栈中元素个数，`s[1]~s[ s[0] ]`为栈中各个元素，于是可以简单地实现：

入栈:`s[++s[0]]=x;`

出栈:`s[0]--;`

取栈顶：`x=s[s[0]];`

用数组模拟栈实现单调栈的代码如下。此处实现的是自底向顶单调递减的单调栈。注意，我
们在栈中通常存储元素的下标/地址，以便于进行与元素顺序有关的统计。

```cpp
void insert(int* val,int* s,int idx){ //val为存放序列值的数组，s为单调栈，idx
                                      //为将要加入元素在val数组中的下标
  while(s[0]!=0 && val[s[s[0]]] < val[idx]) s[0]--;
  s[++s[0]]=x;
}
```
例题：[BZOJ-1012][1]
## 单调队列
To Be Done

 [1]:http://www.lydsy.com/JudgeOnline/problem.php?id=1012