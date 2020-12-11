---
title: hexo的使用
date: 2019-11-25 22:53:21
tags: hexo
categories: 工具
toc: true
keywords: 
description: 
comments: 
---

# hexo

## 安装

```shell
hexo init <folder>
cd <folder>
npm install
```

## 命令

```shell
#命令用于初始化本地文件夹为网站的根目录
hexo init [folder]
 
#新建文章
hexo new [文章类型] <标题>
 
#生成静态文件
hexo generate
hexo g
 
#启动服务器
hexo s
hexo server
 
#部署网址
hexo d
hexo deploy
 
#清理缓存文件
hexo clean
 
#监视文件
hexo w
 
#新建页面
hexo new page "tags"
```



next主题

## 调整hexo页面宽度

 打开/Hexo/themes/hexo-theme-next/source//css/_variables/custom.styl 添加两行代码即可： 

```
$main-desktop = 1200px 
$content-desktop = 900px
```

## 本地搜索功能

安装插件：

```
npm install hexo-generator-searchdb --save
```

修改 站点配置文件_config.yml 

```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

修改主题配置文件_config.yml

```
local_search:
  enable: true
```

## 文章中插入图片的方法

1.  **设置站点配置`_config.yml`**:将`post_asset_folder: false`改为`post_asset_folder: true` 
2.  **安装插件**:`npm install https://github.com/CodeFalling/hexo-asset-image -- save` 

3. 配置typora

   ![1574954911889](hexo%E7%9A%84%E4%BD%BF%E7%94%A8/1574954911889.png)

```
../../source/_posts//${filename}
```

## 报错

1.

> Accessing non-existent property ‘lineno’ of module exports inside circular dependency

![在这里插入图片描述](hexo%E7%9A%84%E4%BD%BF%E7%94%A8/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTAyNjM0MjM=,size_16,color_FFFFFF,t_70.png)

版本：

换一个低版本的Node，我换成`Node 12.14.0`

