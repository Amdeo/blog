---
title: javaScript
toc: true
comments: true
date: 2020-09-28 09:41:49
tags: [javascript]
categories:
keywords:
description:
---

## js中函数定义方式

函数声明

```javascript
function func(param){
//somethings
}
```

函数表达式

```javascript
var func = function(a,b) {
	//somthings
}
```

函数构造函数

```javascript
var func = new Function('param1','parma2','somethings');

var x = func(1,2);
```

自调用函数 （不需要调用自己会执行）

```javascript
(function () {
	//somethings
})();
```

箭头函数

```javascript
const func = (params) => {
	//函数体
}
```

