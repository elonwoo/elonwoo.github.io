---
title: Turn Browser Auto Complete Off
layout: blog.njk
date: 2021-02-26
tags: blog
categories:
  - chrome
---

现在的项目中，所有的页面在在input的中输入过的数据会被浏览器保存着，点击或者双击input就会出现之前输入过的数据。

现在需要让浏览器不保存这些数据，尤其是在登录页面不能保存这些数据。

在input中添加这个参数：autocomplete="off"就可以的了

```html
<input type="text" autocomplete="off"/>
```