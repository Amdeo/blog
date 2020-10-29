---
title: zsh
date: 2019-12-05 23:34:32
tags: zsh
categories: 工具
toc: true
keywords:
description:
comments: 
---
## 查看当前环境shell


```shell
echo $SHELL
```


## 查看系统自带那些shell


```
cat /etc/shells
```


## 安装zsh


```shell
yum -y instal zsh #centos 安装zsh

pacman -S zsh #arch 安装zsh
```

## zsh配置文件

```shell
#配置文件
cat $HOME/.zshrc

# 修改主题
ZSH_THEME="robbyrussell"
```

## 将zsh设置为默认shell


```shell
chsh -s /bin/zsh
```


## 安装oh-my-zsh


自动安装


```shell
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```


zsh主题


```shell
# ls ~/.oh-my-zsh/themes
```


## 插件


### zsh-syntax-highlighting


```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh/zsh-syntax-highlighting
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```


```shell
source ~/.zsh/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```


#### zsh-autosuggestions


```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
```


Add the following to your .zshrc:


```shell
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
```



