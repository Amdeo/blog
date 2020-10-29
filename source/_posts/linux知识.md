---
title: linux知识收集
date: 2019-12-05 22:18:04
tags: linux
categories: 操作系统
toc: true
keywords:
description:
comments: true
---

# LAMP和LNMP区别是什么？

LAMP==Linux+Apache+Mysql+PHP

LNMP==Linux+Nginx+Mysql+PHP

LAMP是Linux+Apache+Mysql+PHP的组合方式，用的是Linux；LNMP是Linux+Nginx+Mysql+PHP的组合方式，其特点是利用Nginx的快速与轻量级，替代以前的LAMP(Linux+Apache+Mysql+PHP)的方式。由于安装方便，并且安装脚本也随时更新。

LAMP使用的是Apache，Apache是世界是用排名第一的[Web服务器](https://www.baidu.com/s?wd=Web服务器&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)软件，其几乎可以在所有广泛使用的计算机平台上运营，由于其跨平台和安全性被广泛使用，是最流行的Web服务端软件之一。

LNMP使用的是Nginx，Nginx是一款高性能额Http和反向代理服务器，也是一个AMAP/POP3/SMTP服务器，Nginx是由Igor Sysoev为俄罗斯访问量第二的Rambler.ru站点开发的，第一个公开版本0.1.0发布于2004年10月4日，2011年6月1日，nginx 1.0.4发布。





### nginx使用

命令

```
nginx -s reopen #重启Nginx

nginx -s reload #重新加载Nginx配置文件，然后以优雅的方式重启Nginx

nginx -s stop #强制停止Nginx服务

nginx -s quit #优雅地停止Nginx服务（即处理完所有请求后再停止服务）

nginx -t #检测配置文件是否有语法错误，然后退出

nginx -?,-h #打开帮助信息

nginx -v #显示版本信息并退出

nginx -V #显示版本和配置选项信息，然后退出

nginx -t #检测配置文件是否有语法错误，然后退出

nginx -T #检测配置文件是否有语法错误，转储并退出

nginx -q #在检测配置文件期间屏蔽非错误信息

nginx -p prefix #设置前缀路径(默认是:/usr/share/nginx/)

nginx -c filename #设置配置文件(默认是:/etc/nginx/nginx.conf)

nginx -g directives #设置配置文件外的全局指令

killall nginx #杀死所有nginx进程
```

