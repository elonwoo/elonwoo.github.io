---
title: Vivium Theme
layout: blog.njk
date: 2021-02-21
tags: blog
categories:
  - chrome
---

``` css
.vimiumReset,
div.vimiumReset,
span.vimiumReset,
table.vimiumReset,
a.vimiumReset,
a:visited.vimiumReset,
a:link.vimiumReset,
a:hover.vimiumReset,
td.vimiumReset,
tr.vimiumReset {
    font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', HelveticaNeue, sans-serif;
}


#vomnibar {
    border-radius: 0;
    border: 0;
    box-shadow: 0 2px 16px rgba(0,0,0,0.3);
    color: #2d2d2d;
    left: 50%;
    margin-left: -320px;
    max-width: 640px;
    top: 18px;
}

#vomnibar .vomnibarSearchArea {
    background: #F9FAF9;
    border: 0;
    border-radius: 0;
    padding: 0;
}

#vomnibar input {
    border-radius: 0;
    border: 0;
    box-shadow: none;
    font-size: 24px;
    height: initial;
    padding: 16px 24px;
}

#vomnibar ul {
    background: #F4F3F4;
    border-radius: 0;
    padding: 0;
}

#vomnibar li {
    border: 0;
    color: #2d2d2d;
    display: flex;
    line-height: 1;
    padding: 4px 16px 4px 24px;
}

#vomnibar li:first-of-type {
    border-top: 1px solid #3175ce;
}

#vomnibar li .vomnibarTopHalf,
#vomnibar li .vomnibarBottomHalf {
    font-size: 13px;
    margin: 0;
    padding: 0;
}

#vomnibar li .vomnibarTopHalf {
    display: flex;
    flex: 0 0 67%;
    margin-right: 16px;
}

#vomnibar li .vomnibarBottomHalf {
    flex: 0 0 33%;
    overflow: hidden;
    text-overflow: ellipsis;
}

#vomnibar li .vomnibarSource.vomnibarNoInsertText,
#vomnibar li .vomnibarSource.vomnibarInsertText {
    display: none;
}

#vomnibar li .vomnibarSource,
#vomnibar li .vomnibarUrl {
    color: #979797;
}

#vomnibar li .vomnibarSource {
    display: block;
    flex-shrink: 0;
    font-size: 13px;
    line-height: 1.6;
    margin-right: 12px;
    text-transform: uppercase;
}

#vomnibar li .vomnibarTitle,
#vomnibar li .vomnibarUrl {
    line-height: 1.6;
}

#vomnibar li .vomnibarTitle {
    color: #2d2d2d;
    display: block;
    margin: 0;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}

#vomnibar li .vomnibarMatch {
    color: inherit;
}

#vomnibar li.vomnibarSelected {
    background: #0b56cd;
}

#vomnibar li.vomnibarSelected .vomnibarSource,
#vomnibar li.vomnibarSelected .vomnibarUrl {
    color: #689cde;
}

#vomnibar li.vomnibarSelected .vomnibarTitle {
    color: #f4f3f4;
}

#vomnibar li.vomnibarSelected .vomnibarMatch {
    color: inherit;
}
```