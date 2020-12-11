---
title: nvm
toc: true
comments: true
date: 2020-11-24 09:33:33
tags:
categories:
keywords:
description:
---

## Mac 安装nvm

```ruby
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

or

```ruby
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

## 命令

```
# 显示所有可用的版本
nvm list

# 安装版本
nvm install 11.13.0

# 使用版本
nvm use 11.13.0

# 卸载版本
nvm uninstall 11.13.0

# 显示node是运行在32位还是64位
nvm arch

# 安装node
nvm install 11.13.0 [arch]

# 开启node.js版本管理
nvm on/off

# 设置下载代理
nvm proxy [url]
```

### 下载node太慢

Macos

```
NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node
```

windows

到nvm安装的目录中settings.txt中，添加：

```
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```





