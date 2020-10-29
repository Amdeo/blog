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

![image-20200620214020985](linux%E4%B8%8B%E8%BF%9B%E7%A8%8B%E5%A0%86%E6%A0%88%E6%9F%A5%E7%9C%8Bgstack/image-20200620214020985.png)