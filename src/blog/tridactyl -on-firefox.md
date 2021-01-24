---
title: Tridactyl on Firefox
layout: blog.njk
date: 2020-01-20
tags: blog
categories:
  - firefox
---

![Tridactyl-on-Firefox](https://gt-toolbox.oss-cn-beijing.aliyuncs.com/uPic/j1kuJm.png)

```text

" For syntax highlighting see https://github.com/tridactyl/vim-tridactyl
" vim: set filetype=tridactyl
" Plug 'tridactyl/vim-tridactyl'


" ====================环境变量====================
set yankto both
set putfrom selection

set allowautofocus false
set viewsource default

" Sometimes the status bar in the bottom left corner overlaps the Tridactyl
" command line, so set an option to move the status bar to the right.
guiset_quiet hoverlink right
guiset_quiet tabs count

" 新标签页设置
set newtab https://www.google.com/ncr

" 使用浏览器默认搜索
unbind <C-f>

" 但也支持 Tridactyl 搜索
bind / fillcmdline find
bind ? fillcmdline find -?
bind n findnext 1
bind N findnext -1

" 平滑滚动
set smoothscroll true

" hint按键
set hintchars "arstdhneiowfpluy"


" ====================便捷书签====================
quickmark v https://www.v2ex.com/



" ====================键盘映射====================
bind q tabprev
bind w tabnext
bind Q tabmove -1
bind W tabmove +1
bind h back
bind l forward
bind j scrollline 50
bind k scrollline -50

bind c current_url open
bind C current_url tabopen

unbind --mode=normal m
bind m pin

" make d take you to the tab you were just on (I find it much less confusing)
bind d composite tab #; tabclose #
bind D tabclose

" Handy multiwindow/multitasking binds
bind gd tabdetach
bind gD composite tabduplicate; tabdetach

" Make yy use canonical / short links on the 5 websites that support them
unbind --mode=normal y
bind yy clipboard yankcanon
bind yt composite js document.title + '\n' + document.location.href | yank

" swap p and P
bind p clipboard tabopen
bind P clipboard open

" TODO reload config with :source?


bind --mode=normal <C-P> winopen -private
bind --mode=ex     <C-a> text.beginning_of_line
bind --mode=insert <C-a> text.beginning_of_line
bind --mode=input  <C-a> text.beginning_of_line
bind --mode=ex     <C-e> text.end_of_line
bind --mode=insert <C-e> text.end_of_line
bind --mode=input  <C-e> text.end_of_line
bind --mode=ex     <C-f> text.forward_word
bind --mode=insert <C-f> text.forward_word
bind --mode=input  <C-f> text.forward_word
bind --mode=ex     <C-k> text.kill_line
bind --mode=insert <C-k> text.kill_line
bind --mode=input  <C-k> text.kill_line
bind --mode=ex     <C-u> text.backward_kill_line
bind --mode=insert <C-u> text.backward_kill_line
bind --mode=input  <C-u> text.backward_kill_line
bind --mode=ex     <C-V> composite getclip selection | text.insert_text
bind --mode=insert <C-V> composite getclip selection | text.insert_text
bind --mode=input  <C-V> composite getclip selection | text.insert_text
bind --mode=ex     <C-w> text.backward_kill_word
bind --mode=insert <C-w> text.backward_kill_word
bind --mode=input  <C-w> text.backward_kill_word



" ====================搜索引擎====================
" ** Search Engines
" Disable all searchurls
jsb Object.keys(tri.config.get("searchurls")).reduce((prev, u) => prev.catch(()=>{}).then(_ => tri.excmds.setnull("searchurls." + u)), Promise.resolve())

set searchengine g
" set searchurls.KEYWORD URL
set searchurls.b https://www.baidu.com/s?ie=UTF-8&wd=%s
set searchurls.d https://www.douban.com/search?q=%s
set searchurls.g https://www.google.com/search?q=%s
set searchurls.gh https://github.com/search?utf8=%E2%9C%93&q=%s&ref=simplesearch
set searchurls.mdn https://developer.mozilla.org/en-US/search?q=%s&topic=api&topic=js
set searchurls.npm https://www.npmjs.com/search?q=%s
set searchurls.pydoc https://docs.python.org/3/search.html?q=%s
set searchurls.r https://old.reddit.com/r/%s
set searchurls.rustdoc https://doc.rust-lang.org/std/index.html?search=%s
set searchurls.y https://www.youtube.com/results?search_query=%s



" ====================脚本调用====================
" :js
" urlmodify
alias tabsort jsb browser.tabs.query({}).then(tabs => tabs.sort((t1, t2) => t1.url.localeCompare(t2.url)).forEach((tab, index) => browser.tabs.move(tab.id, {index})))
alias tabuniq jsb browser.tabs.query({}).then(tabs => browser.tabs.remove(tabs.filter((tab, index) => tabs.slice(index + 1).find(t => t.url == tab.url)).map(tab => tab.id)))
bind --mode=normal ee composite get_current_url | exclaim /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome


" ====================例外设置====================
autocmd DocStart mail.google.com mode ignore



" ====================其他设置====================
" Add helper commands that Mozillians think make Firefox irredeemably
" insecure. For details, read the comment at the top of this file.
command fixamo_quiet jsb tri.excmds.setpref("privacy.resistFingerprinting.block_mozAddonManager", "true").then(tri.excmds.setpref("extensions.webextensions.restrictedDomains", '""'))
command fixamo js tri.excmds.setpref("privacy.resistFingerprinting.block_mozAddonManager", "true").then(tri.excmds.setpref("extensions.webextensions.restrictedDomains", '""').then(tri.excmds.fillcmdline_tmp(3000, "Permissions added to user.js. Please restart Firefox to make them take affect.")))

" Make Tridactyl work on more sites at the expense of some security. For
" details, read the comment at the top of this file.
fixamo_quiet



```