---
qtitle: css
toc: true
comments: true
date: 2020-11-24 10:01:55
tags:
categories: css
keywords:
description:
---

# CSS

> 层叠样式表(Cascading Style Sheets)，样式定义如何显示html

如何使用CSS？

## 外部引用

在头部中使用link标签引用

```html
<head>
	<link rel="stylesheet" href="xx.css" type="text/css">
</head>
```

`xx.css` 表示样式文件路径

##  嵌入样式

> 使用`<style>`标签引用

```
<style>
p {
	background-color: #fff;
}
</style>
```

## 内联样式

在标签中使用style属性可以定义样式

```
<p style="color:blue">你好</p>
```

### 导入样式

两种方式：

```
@import "xx.css"
@import url("xx.css")
```

在哪使用？

- 在xx.css文件中，可以引用另一个样式文件
- 或者在`<style>`标签中引用

初始样式

> 有些标签默认含有内外边距，且不同浏览器大小也不一样。为了统一我们可以重置标签的CSS默认样式。

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css" />
```

## 选择器

> 计算机所有的概念和技术都是演化的产物，因为需要才会产生，在css中拥有很多选择器，选择器的作用就是定位html标签，不同的选择器代表不同的定位方式。

### 类选择器

```
<p class="example1"></p>

.example1{
	color: #fff;
}
```

`example1`就是定义的类选择器，通过这个选择器，定位所有拥有相同class的标签，注意：类选择器可以很多标签

### ID选择器

>id选择器对应的标签是唯一的，不同于类选择器可以到处使用。

```
<p id="example1"></p>

#example1{
	color: #fff;
}
```

### 标签选择器

```
<p>xx</p>

p{
	color: #fff;
}
```

| 选择器 | 描述             |
| ------ | ---------------- |
| *      | 作用于所有的标签 |
| xx     |                  |
|        |                  |

























