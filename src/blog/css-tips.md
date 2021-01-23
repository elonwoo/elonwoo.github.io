---
title: css tips
layout: blog.njk
tags: blog
date: 2019-07-16
categories:
  - css
---

## 单行文本溢出显示省略号：

```css
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
```

![单行文本溢出显示省略号](http://www.daqianduan.com/wp-content/uploads/2015/10/dome1.png)

## 多行文本溢出显示省略号

```css
display: -webkit-box;
overflow: hidden;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3;
```

![多行文本溢出显示省略号](http://www.daqianduan.com/wp-content/uploads/2015/10/dome2.png)
