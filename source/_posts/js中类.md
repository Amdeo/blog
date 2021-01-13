---
title: js中的面向对象
date: 2019-12-05 23:34:32
tags: zsh
categories: javascript
toc: true
keywords:
description:
comments: 
---

# JavaScript



## 变量提升

```javascript
a = 1;
var a;
console.log(a);
```

输出结果: 1，按照其他语言的特性来说，a没有声明就使用，会报错，这里`var a;`声明了变量，`var a;这个动作会提升至作用域的最上面，所有a不是未声明。`

