---
title: linux下进程堆栈查看gstack
date: 2020-06-20 21:34:55
tags:
categories:
toc: true
keywords:
description:
comments: true
---

## gstack安装

```shell
yum install gdb -y
```

## 使用

```shell
gstack pid
```

先获取需要查看的进程 ps -ef

```shell
gstack 29913
```

![image-20200620214020985](https://gitee.com/Cooper001/blog-img/raw/master/img/image-20200620214020985.png)