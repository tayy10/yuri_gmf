---
layout: post
title: Jekyll 编译后head标签里面的内容错位到body中
categories: jekyll
tag: [bug, jekyll]
excerpt_separator: <!--more-->
description: Jekyll 编译后head标签里面的内容错位到body中
keywords: head,body,错位,jekyll
---
# Jekyll神坑

先说说百度到的最多的说法：
1. 文件编码格式问题：UTF-8 without BOM
自己检测文件编码无问题，错位未解决

2. 标签未闭合
自己检测标签都已闭合，错位未解决
<!--more-->

## 自己解决方法
具体怎么解决的自己也说不清楚，估计原因
- 标签顶格写

- 缩进使用Tab，切勿使用空格代替

示例代码如下：
```html
<!DOCTYPE html>
<html lang="en">
<head>
    ...
</head>
<body>
    ...
</body>
</html>
```

