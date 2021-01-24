---
title: Vimperator on Firefox
layout: blog.njk
date: 2020-01-18
tags: blog
categories:
  - firefox
---

```text

loadplugins
source! ~/.vimperatorrc.local

"" ================colorscheme配色方案=====================
colorscheme vimpwhite

"" ==================环境变量设置========================

"自动补全，s=搜索引擎和关键词，f＝本地文件，l＝书签和历史，b＝书签，h＝历史，S＝搜索引擎建议，t＝打开的标签
set complete=slSt
set defsearch=g
set titlestring=firefox
"set newtab=all
"Show the destination of the link under the cursor in the status bar.
set ssli=1
set gui=nonavigation
set gui=none
set editor="/Applications/MacVim.app/Contents/MacOS/Vim -g -f"

map x :set gui=none,tabs,bookmarks<CR>
map c :set gui=none,tabs<CR>

map <C-Up> :set gui=all<CR>
map <C-Left> :set gui=none<CR>
map <F3> :set gui=none<CR>
map <C-Right> :set gui=none,tabs<CR>
map <F4> :set gui=none,tabs<CR>

set scrollbars=false
set hintchars=qwertasdfgzxcvb
set hlsearch
set focuscontent
style -name commandline-ime chrome://* #liberator-commandline-command input {ime-mode: inactive;} 

com! -nargs=? -complete=search switchenginesearch exe 'o <args> ' + (buffer.lastInputField?buffer.lastInputField.value:'')
map s gi<ESC> :switchenginesearch<Space>


"" =====================键盘映射======================
noremap q gT
noremap w gt
noremap Q :tabmove! -1<CR>
noremap W :tabmove! +1<CR>
map < g0
noremap > g$
map h :back<CR>
map l :forward<CR>

noremap j 8j
noremap k 8k
noremap J <C-d>
noremap K <C-u>


" inoremap <C-a> <Ins><C-a><Ins>
map <C-b> i<C-b>
noremap gi gi<C-e>

map U :u<space>
noremap V :emenu<space>
noremap pp P
map S :stop<CR>

noremap ,g :tabopen<space>g<space>
noremap ,b :tabopen<space>b<space>
noremap ,d :tabopen<space>d<space>
noremap ,j :tabopen<space>j<space>
noremap ,r :tabopen<space>r<space>
noremap ,t :tabopen<space>t<space>
noremap ,m :tabopen<space>gm<space>
noremap ,y :tabopen<space>y<space>

map ge <C-6>

map <C-t> gH
map gR :restart<CR>


"=================about:config=======================
" set!network.proxy.socks_remote_dns=true
" set!mousewheel.withnokey.sysnumlines=false
" set!mousewheel.withnokey.numlines=10
" set!layout.spellcheckDefault=0
" set!browser.download.manager.scanWhenDone=false
" set!dom.max_script_run_time=20
" set!security.dialog_enable_delay=0
set!middlemouse.paste=true
" set!browser.tabs.closeWindowWithLastTab=false
set!clipboard.autocopy=true
" set!browser.sessionstore.restore_pinned_tabs_on_demand=true
" set!browser.tabs.insertRelatedAfterCurrent=true

"===================Vimp插件========================
let g:smooziee_scroll_amount="400"
let g:smooziee_scroll_interval="10"

map Y :copy titleAndURL<CR>
map eY :copy markdownLink<CR>
"==================外部程序调用=======================
" command! ie js liberator.execute('!start iexplore ' + buffer.URL)
map ee :js io.run("/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome", [buffer.URL])<CR>

map eso :source ~/.vimperatorrc<CR>


"=====================qmark========================
silent qmark w http://www.163.com/


"＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝＝待查看=======================
"Tree Style Tab 标签显示数字编号
" set tabnumbers=true
map <C-f>h/j/k/l :set!extensions.treestyletab.tabbar.position=left/bottom/top/right


" "javascript to hide statusbar
" noremap <silent> <F2> :js toggle_bottombar()<CR>
" noremap : :js toggle_bottombar('on')<CR>:
" noremap o :js toggle_bottombar('on')<CR>o
" noremap O :js toggle_bottombar('on')<CR>O
" noremap t :js toggle_bottombar('on')<CR>t
" noremap T :js toggle_bottombar('on')<CR>t
" noremap / :js toggle_bottombar('on')<CR>/
" cnoremap <CR> <CR>:js toggle_bottombar('off')<CR>
" cnoremap <Esc> <Esc>:js toggle_bottombar('off')<CR>
" 
" :js << EOF
" function toggle_bottombar(p) {
"     var bb = document.getElementById('liberator-bottombar');
"     if (!bb)
"         return;
"     if (p == 'on'){
"         bb.style.height = '';
"         bb.style.overflow = '';
"         return;
"     }
"     if (p == 'off'){
"         bb.style.height = '0px';
"         bb.style.overflow = 'hidden';
"         return;
"     }
"     bb.style.height = (bb.style.height == '') ? '0px' : '';
"     bb.style.overflow = (bb.style.height == '') ? '' : 'hidden';
" }
" toggle_bottombar();
" EOF
" 
" "keep the status line visible in full-screen
" au Fullscreen .* :set guioptions+=s

```