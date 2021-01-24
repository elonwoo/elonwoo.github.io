---
title: Pentadactyl on Pale Moon
layout: blog.njk
date: 2020-01-19
tags: blog
categories:
  - firefox
---

![Pentadactyl-on-Palemoon](https://gt-toolbox.oss-cn-beijing.aliyuncs.com/cnAYuE-HRASwW.png)

```text

"1.3.1

loadplugins '\.(js|penta)$'
group user
set cdpath=''

" vim: set ft=pentadactyl:

"" ==================环境变量设置========================

set complete=search,location,file,bookmark,history,suggestion
set defsearch=g
set titlestring=firefox
"set newtab=all
"Show the destination of the link under the cursor in the status bar.
set editor="/Applications/MacVim.app/Contents/MacOS/Vim -g -f"
set hintkeys=qwertasdfgzxcvb


"" =====================键盘映射======================
" map x :set gui=none,tabs,bookmarks<CR>
" map c :set gui=none,tabs<CR>
" 
" map <C-Up> :set gui=all<CR>
" map <C-Left> :set gui=none<CR>
" map <F3> :set gui=none<CR>
" map <C-Right> :set gui=none,tabs<CR>
" map <F4> :set gui=none,tabs<CR>

map -b q gT
map -b w gt
map -b Q :tabmove! -1<CR>
map -b W :tabmove! +1<CR>
map < g0
map -b > g$
map h :back<CR>
map l :forward<CR>

map -b j 8j
map -b k 8k
map -b J <C-d>
map -b K <C-u>


" inoremap <C-a> <Ins><C-a><Ins>
map -b gi gi<C-e>

map U :u<space>
map -b V :emenu<space>
map -b pp P
map S :stop<CR>

map -b ,g :tabopen<space>g<space>
map -b ,b :tabopen<space>b<space>
map -b ,d :tabopen<space>d<space>
map -b ,j :tabopen<space>j<space>
map -b ,r :tabopen<space>r<space>
map -b ,t :tabopen<space>t<space>
map -b ,m :tabopen<space>gm<space>
map -b ,y :tabopen<space>y<space>

map ge <C-6>

map <C-t> gH
map gR :restart<CR>

map -b Y :js dactyl.clipboardWrite(buffer.title + '\n' + buffer.URL)<CR>
map -b eY :js dactyl.clipboardWrite('[' + buffer.title + '](' + buffer.URL + ')' )<CR>

"==================外部程序调用=======================
map -b ee :js io.run("/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome", [buffer.URL])<CR>
map -b eso :source ~/.pentadactylrc<CR>

"=====================qmark========================
silent qmark v https://www.v2ex.com/

```