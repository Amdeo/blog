---
title: 原样输出html标签
date: 2019-12-21 22:50:50
tags: [html,前端]
categories: 前端
toc: true
keywords:
description: 在网页中输出html源码
comments: 
---

转载：https://www.cnblogs.com/jiayu123/p/10612852.html

第一种

```html
<script type="text/html" style='display:block'>
<div class="banner-text p-5">
<div class="container">
<div class="banner-text-con">
<div>
<h1 style="color:;">html代码不被解析</h1>
</div>
</div>
</div>
</div>
</script>
```

第二种：

```html
<xmp>
xxx
</xpm>
```

第三种

```html
<textarea style="width:'800px';height:300px;">
xxxx
</textarea>
```

注意的是记得写display:block，不然没有效果的，直接输出，没有任何格式化效果

第四种

如果是有空格和回车这样的特殊字符的简单文本可以使用`<pre>` `</pre>`标签

第五种

将<>转换成特殊字符`<` 转化为`&lt`, `>` 转化为`&gt`。



