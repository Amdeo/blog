---
title: 解决git网速慢的办法
date: 2018-11-25 22:53:21
tags: git
categories: git
toc: true
keywords: 
description: 
comments: 
---

### 原因
GitHub被墙屏蔽了

### 解决方法
绕过dns解析，在本地直接绑定host，该方法也可加速其他因为CDN被屏蔽导致访问慢的网站。

### 实现
在本地host文件中添加映射，步骤如下：

1.  用文本编辑器打开hosts文件，位于C:\Windows\System32\drivers\etc目录下

2.  打开 [http://tool.chinaz.com/dns](http://tool.chinaz.com/dns) ,这是一个查询域名映射关系的工具

3.  查询 github.global.ssl.fastly.net 和 assets-cdn.github.com 两个地址

4.  多查几次，选择一个稳定，延迟较低的 ip 按如下方式添加到host文件

5.  保存文件，重新打开浏览器，起飞。

```
  ......
 # For example:
 #
 # 102.54.94.97 rhino.acme.com # source server
 # 38.25.63.10 x.acme.com # x client host
 # localhost name resolution is handled within DNS itself.
 # 127.0.0.1 localhost
 # ::1 localhost
 # github
 192.30.253.112 assets-cdn.github.com
 151.101.88.249 github.global.ssl.fastly.net
```