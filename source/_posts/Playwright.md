---
title: Playwright
date: 2021-03-05 22:09:22
tags: [python,编程语言]
categories: python
toc: true
keywords:
description:
comments: true
---

# Playwright

Playwright是一个强大的Python库，仅用一个API即可自动执行 Chromium 、 Firefox 、 WebKit 等主流浏览器自动化操作，并同时支持以 无头模式 、 有头模式 运行。

Playwright提供的自动化技术是绿色的、功能强大、可靠且快速，支持 Linux 、 Mac 以及 Windows 操作系统。

[项目地址](https://github.com/microsoft/playwright)

[文档地址](https://playwright.dev/python/)

## 安装

安装playwright-python依赖库（需要Python3.7以上）

```shell
pip3 install playwright
```

安装主流的浏览器驱动

```shell
python3 -m playwright install 
```

## 录制功能

这个工具与常用selenium等其他工具的区别，就是其录制功能

```
python -m playwright codegen --help
```

![image-20210312092809080](https://gitee.com/Cooper001/blog-img/raw/master/img/image-20210312092809080.png)

```
python -m playwright codegen --target=python -o test.py -b chromium https://www.baidu.com
```

![image-20210312093149634](https://gitee.com/Cooper001/blog-img/raw/master/img/image-20210312093149634.png)

最终在本地生成test.py文件

![image-20210312093246755](https://gitee.com/Cooper001/blog-img/raw/master/img/image-20210312093246755.png)