---
title: 生成和调试core文件
date: 2017-03-16 21:21:30
tags: 调试
categories: 工具
toc: true
keywords: gdb
description: 生成和调试core文件
comments: 
---

# core dump的产生

core文件又称为内核转储文件，它是进程运行时突然崩溃的那一刻的内存快照

作用：

(1) 内核转储的最大好处是能够保存问题发生时的状态。
(2) 只要有可执行文件和内核转储，就可以知道进程当时的状态。
(3) 只要获取内核转储，那么即使没有复现环境，也能调试。

配置操作系统的内核转储功能

(1) 查看当前转储文件大小

```
ulimit -c
```

输出的结果为0，表示没有启动内核转储。

(2) 开启内核转储

在/etc/profile 然后，在profile中添加下面这些命令

```
ulimit -c unlimited  #设置coredump 大小为无限大

ulimit -c 1073741824      --1G大小
```

source /etc/profile 就会永久生效

(3) 指定内核转储的文件名和目录

`如果没有配置一般会生成的位置和运行程序的路径相同`

可以通过在/etc/sysctl.conf文件中，对sysctl变量kernel.core_pattern的设置。

在sysctl.conf文件中添加下面两句话：

```
kernel.core_pattern = /var/core/core_%e_%p
kernel.core_uses_pid = 0
```

这里%e, %p分别表示：
%c 转储文件的大小上限
%e 所dump的文件名
%g 所dump的进程的实际组ID
%h 主机名
%p 所dump的进程PID
%s 导致本次coredump的信号
%t 转储时刻(由1970年1月1日起计的秒数)
%u 所dump进程的实际用户ID

可以使用以下命令，使修改结果马上生效。

```
sysctl –p /etc/sysctl.conf
```

# 调试core dump

示例程序:

```C++
#include "stdio.h"
#include "stdlib.h"

void dumpCrash()
{
    char *pStr = (char *)"test_content";
    free(pStr); //使用free释放栈或者常量区，程序就会core dump
}
int main()
{
    dumpCrash();
    return 0;
}
```

gdb打开core文件

```
gdb 可执行程序 core文件
```

![image-20200316215341036](%E7%94%9F%E6%88%90%E5%92%8C%E8%B0%83%E8%AF%95core%E6%96%87%E4%BB%B6/image-20200316215341036.png)

查看coredump时的堆栈

使用bt或者where命令

![image-20200316215908758](%E7%94%9F%E6%88%90%E5%92%8C%E8%B0%83%E8%AF%95core%E6%96%87%E4%BB%B6/image-20200316215908758.png)

可以从第四帧开始看，因为上面的一看就是调用动态库中的代码，不是我们的代码。

![image-20200316220146910](%E7%94%9F%E6%88%90%E5%92%8C%E8%B0%83%E8%AF%95core%E6%96%87%E4%BB%B6/image-20200316220146910.png)

`f 4`跳转到第四帧上

执行`disassemble`,打开该帧的反汇编代码。

![image-20200316220406667](%E7%94%9F%E6%88%90%E5%92%8C%E8%B0%83%E8%AF%95core%E6%96%87%E4%BB%B6/image-20200316220406667.png)

如上箭头位置标示coredump该函数调用的位置

使用下面的命令去掉函数的名词修饰

```
shell echo free@plt |C++filt
```

![img](%E7%94%9F%E6%88%90%E5%92%8C%E8%B0%83%E8%AF%95core%E6%96%87%E4%BB%B6/Center.png)

当然这里使用去掉名词修饰效果和之前还是一样的，在虚函数的调试中就很大作用了。

我们下面可以推测，是调用free函数才出现的问题。