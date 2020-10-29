---
title: 在私人服务器创建git仓
date: 2019-11-26 22:46:01
tags: git
categories: git
toc: true
keywords:
description: 在服务器上创建私有git远程仓库
comments: 
---

## 安装GIT


创建git账户并登录，直接指定用户目录到/home/git

## 创建git用户

```
useradd git -d /home/git -m -s /bin/bash
su git
```

## 创建仓库

```shell
cd ~
git init --bare mygit.git
```

## 设置SSH Key

在客户端和服务端都执行下

```
ssh-keygen -t rsa //生成密钥对
id_rsa.pub传到服务器上，执行cat id_rsa.pub >> ~/.ssh/authorized_keys
```

## git clone

```shell
git clone git@<服务器公网IP>:/home/git/myserver.git
```

## 数据仓库的迁移

增加一个远端仓库

![1574780797750](%E5%9C%A8%E7%A7%81%E4%BA%BA%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%88%9B%E5%BB%BAgit%E4%BB%93/1574780797750.png) 

推送时选择新增的地址
![1574780839801](%E5%9C%A8%E7%A7%81%E4%BA%BA%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%88%9B%E5%BB%BAgit%E4%BB%93/1574780839801.png)


## 问题

### 利用公钥私钥解决Linux中git clone git库需要输入密码的问题

```shell
chmod 700 .ssh
chmod 600 .ssh/authorized_keys
```

git上的仓库对git用户要有写权限，同时需要将/etc/ssh/sshd_config中将RSA认证打开,即

```shell
RSAAuthentication yes
 
PubkeyAuthentication yes
 
AuthorizedKeysFile .ssh/authorized_keys
```

home/git属于git用户所有，且权限为755即drwxr-xr-x。