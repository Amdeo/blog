---
title: C陷阱
date: 2016-03-15 23:44:07
tags:
categories:
toc: true
keywords:
description:
comments: true
---

## 数组作为函数参数，不能使用sizeof获取数组个数

```C++
#include <iostream>
#include <stdio.h>

using namespace std;

void test (int *b)
{
    int i=0;
    printf("%d\n",sizeof(b));
}

int main(int argc, char const *argv[])
{
    /* code */
    int a[10]={2,4,6,8,10,12,14,16,18,20};
    printf("%d\n",sizeof(a));
    test(a);
    putchar('\n');
    return 0;
}
```

输出:

```
40
8
```

因为数组作为函数参数，只是将指向数组指针拷贝给函数，所以在函数中使用sizeof，只能获取指针的内存大小。