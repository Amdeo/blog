---
title: C++仿函数
date: 2020-05-17 19:36:04
tags: C++
categories: C++
toc: true
keywords: C++
description: 仿函数的简介
comments: 
---

# 仿函数
所谓的仿函数，使用过重载()运算符模拟函数行为的类型
1. 仿函数不是函数，是一个类
2. 仿函数重载()运算符，使得代码形式好像调用函数

```C++
#include <iostream>

class myclass
{
public:
    explicit myclass(int n) : threshold(n) {}
    bool operator()(int n)
    {
        return n > threshold ? true : false;
    }

private:
    int threshold;
};

int main(int argc, char const *argv[])
{
    using namespace std;
    myclass a(10);

    cout << a(2) << endl;
    return 0;
}
```
