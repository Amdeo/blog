---
title: python常用库
date: 2019-12-05 22:09:22
tags: [python,编程语言]
categories: python
toc: true
keywords:
description:
comments: true
---

## JSON

#### json.dumps

> 将Python对象编码成JSON字符串

```python
import json

data = [ { 'a' : 1, 'b' : 2, 'c' : 3, 'd' : 4, 'e' : 5 } ]

data2 = json.dumps(data)
print(data2)
```

json.loads

> 用于将JSON数据转化为Python字符串的数据类型

```python
import json

jsonData = '{"a":1,"b":2,"c":3,"d":4,"e":5}';

text = json.loads(jsonData)
print(text)
```

## zlib

> 数据压缩

