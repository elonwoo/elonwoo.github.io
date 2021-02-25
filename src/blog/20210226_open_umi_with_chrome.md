---
title: Open Umi With A Specific Browser
layout: blog.njk
date: 2021-02-26
tags: blog
categories:
  - chrome
---

推荐一个 Github 项目「Finicky」，可以通过设置关键词让特定浏览器打开特定网页，完美解决我想要用 Firefox 打开 RoamResearch  但默认是 Chrome 的问题
[johnste/finicky: A macOS app for customizing which browser to start](https://github.com/johnste/finicky)

但我的需求较为简单，平常已经全面使用Vivaldi Browser，用umijs做开发时，用Chrome打开调试

编辑 `package.json`

```javascript
"start": "cross-env ESLINT=none DEBUG_MODE=true PORT=8005 umi dev",
```

修改为

```javascript
"start": "cross-env ESLINT=none DEBUG_MODE=true BROWSER='google chrome' PORT=8005 umi dev",
```