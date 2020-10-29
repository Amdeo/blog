---
title: git基础
date: 2017-11-26 23:14:56
tags: git
categories: git
toc: true
keywords: 
description: 
comments: 
---

# Git配置

Git提供一个git config的工具，专门来配置或读取相应的工作环境变量。

- `/etc/gitconfig` 文件：系统中对所有用户普遍适用的配置。
- `~/.gitconfig` 文件：用户目录下的配置文件只适用于该用户。

用户信息

```shell
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

文本编辑器

```shell
$ git config --global core.editor emacs
```

差异分析工具

```shell
$ git config --global merge.tool vimdiff
```

查看配置信息

```shell
git config --list
```

![image-20191220231611951](git%E5%9F%BA%E7%A1%80/image-20191220231611951.png)

查看某个配置

```shell
git config user.name
```

Git获取帮助

例如：

```shell
git help config
```



# Git基础

初始化新仓库

```shell
git init
```

增加文件

```shell
git add *.c
git add README
```

克隆仓库

```shell
git clone url
```

查看git提交历史

```shell
git log
git log -p -2 #-p 选项展开显示每次提交的内容 -2显示最近的两次更
git log --stat #显示简要的增改行数统计
```

| 选项            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| -p              | 按补丁格式显示每个更新之间的差异。                           |
| --word-diff     | 按 word diff 格式显示差异。                                  |
| --stat          | 显示每次更新的文件修改统计信息。                             |
| --shortstat     | 只显示 --stat 中最后的行数修改添加移除统计。                 |
| --name-only     | 仅在提交信息后显示已修改的文件清单。                         |
| --name-status   | 显示新增、修改、删除的文件清单。                             |
| --abbrev-commit | 仅显示 SHA-1 的前几个字符，而非所有的 40 个字符。            |
| --relative-date | 使用较短的相对时间显示（比如，“2 weeks ago”）。              |
| --graph         | 显示 ASCII 图形表示的分支合并历史。                          |
| --pretty        | 使用其他格式显示历史提交信息。可用的选项包括 oneline，short，full，fuller 和 format（后跟指定格式）。 |
| --oneline       | --pretty=oneline --abbrev-commit 的简化用法。                |

```shell
git log --since=2.weeks #显示最近的两周内的提交
```

| 选项              | 说明                         |
| ----------------- | ---------------------------- |
| -(n)              | 仅显示最近的 n 条提交        |
| --since, --after  | 仅显示指定时间之后的提交。   |
| --until, --before | 仅显示指定时间之前的提交。   |
| --author          | 仅显示指定作者相关的提交。   |
| --committer       | 仅显示指定提交者相关的提交。 |

修改最后一次提交

```shell
git commit --amend
```

查看当前仓库基本信息

```shell
git remote -v
git remote show origin
```

显示项目所有分支

```shell
git branch -a
```

显示git修改的内容

```shell
git status
```

增加远程仓库

```shell
git remote add origin "URL"
```



![1574781334458](git%E5%9F%BA%E7%A1%80/1574781334458.png)

### git上传大文件

报错信息：RPC failed; curl 56 OpenSSL SSL_read: SSL_ERROR_SYSCALL, errno 10054

打开git bash增加配置

```shell
git config --global http.postBuffer  524288000
```

