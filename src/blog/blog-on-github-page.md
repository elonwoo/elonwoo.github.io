---
title: Eleventy Blog On GitHub Page
layout: blog.njk
date: 2020-01-23
tags: blog
categories:
  - blog
---
[[TOC]]
## 主题参考
参照 Randy's blog 的主题

[Randy's Blog](https://lutaonan.com/)

[djyde/blog-2020](https://github.com/djyde/blog-2020)


## 注意事项
把整个github的项目下载下来，执行以下命令后就可以启动了

```javascript
yarn

yarn dev

yarn build:css # build css files

yarn build # build the whole project
```

修改自己的个人信息，去除不必要的功能页，上传到自己的Github Page

> 发文新建的markdown文件，文章信息部分需要严格遵守格式

```plaintext
---
title: XXXXXXX
layout: blog.njk
date: XXXX-XX-XX
tags: blog (这里必须是blog)
categories:
  - XXX（这里可以修改）
---
```

## 添加自定义域名
在项目根目录下新建`CNAME`文件，文件填写
```plaintext
your-domain.com
```

编辑 `.eleventy.js` 文件，添加如下
```javascript
// 表示在编译时，把`CNAME`文件加进去，
module.exports = function(eleventyConfig) {
  ...
  eleventyConfig.addPassthroughCopy("CNAME");
  ...
}
```

## 添加Github Action


项目根目录下添加
```plaintext
.github/workflows/build.yml
```

`build.yml` 文件内容如下

```yml
name: Build Eleventy

on:
  push:
    branches:
      - master

jobs:
  build:
    runs-on: ubuntu-20.04

    strategy:
      matrix:
        node-version: [12.x]

    steps:
      - uses: actions/checkout@v2

      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}

      - name: Install dependencies & build
        run: |
          npm i
          npm run build

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          publish_dir: ./_site
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

这样项目每次push到Github后，Github会识别到`build.yml`，会自动构建发布网站，发布成功后，会在Github的项目下新建分支`gh-pages`，也就是会把`_site`里的内容，发布到`gh-pages`分支里

最后我们需要在
GitHub blog项目-Settings-GitHub Pages-Source-Branch设置为gh-pages


## 参考链接
- [How to Deploy Eleventy to GitHub Pages With GitHub Actions :: rockyourcode](https://www.rockyourcode.com/how-to-deploy-eleventy-to-github-pages-with-github-actions/)
- [How To Deploy an Eleventy Site to Github Pages with a Custom Domain | justus.ws](https://www.justus.ws/tech/deploying-eleventy-to-github-pages/#adding-a-cname-file)
- [GitHub Actions 入门教程 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2019/09/getting-started-with-github-actions.html)