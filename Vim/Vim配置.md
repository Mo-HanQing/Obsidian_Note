---
date: 2024-07-07
aliases:
  - Vim
tags:
  - Computer
  - Vim
---
```
" ReMapping-----------------------------------------------------------  
  
" Changed direction keys +++++++++++++++++++++++++++++++++++++++++++++++  
" In normal--------  
nmap i <up>  
nmap j <left>  
nmap k <down>  
nmap l <right>  
nmap u <insert>  
nmap h <undo>  
" In visual--------  
vmap i <up>  
vmap j <left>  
vmap k <down>  
vmap l <right>  
  
" Changed <Esc> to jj ++++++++++++++++++++++++++++++++++++++++++++++++++  
imap jj <Esc>  
  
" Changed <:> to <space> +++++++++++++++++++++++++++++++++++++++++++++++  
nmap <space> :  
  
  
" Changed <insert> to <s> (insert before cursor)  
nnoremap s <insert>  
  
" Changed <o> to <d>  (start a new line and insert)  
nnoremap d o  
  
" Changed <a> to <f> and Delete <a> (insert behind cursor)  
nnoremap f a  
nnoremap a <Nop>  
  
  
" Changed <Ctrl + s> to SaveAll ++++++++++++++++++++++++++++++++++++++++  
nnoremap <C-s> :wa<CR>  
vnoremap <C-s> <Esc>:wa<CR>  
inoremap <C-s> <C-o>:wa<CR>  
  
" Changed Copy to <Ctrl + c> +++++++++++++++++++++++++++++++++++++++++++  
nnoremap <C-c> yy  
vnoremap <C-c> "+y  
inoremap <C-c> <Esc>yy  
  
" Changed Paste to <Ctrl + v> ++++++++++++++++++++++++++++++++++++++++++  
nnoremap <C-v> "+p  
vnoremap <C-v> "+p  
inoremap <C-v> <C-o>"+p  
  
" Changed SelectAll to <Ctrl + a> ++++++++++++++++++++++++++++++++++++++  
map <C-a> ggVG  
  
" Changed "Copy current line to next line" to <Ctrl + d> ++++++++++++++++  
nnoremap <C-d> :t.<CR>  
vnoremap <C-d> :t'>+1<CR>  
inoremap <C-d> <Esc>:t.<CR>  
  
" Changed "Delete current line" to <Ctrl + y> +++++++++++++++++++++++++++  
nnoremap <C-y> dd  
vnoremap <C-y> :d<CR>  
inoremap <C-y> <Esc>dd  
  
" Changed "Undo" to <Ctrl + z> ++++++++++++++++++++++++++++++++++++++++++  
nnoremap <C-z> u  
vnoremap <C-z> u  
inoremap <C-z> <C-o>u  
  
" Changed "Cut" to <Ctrl + x>  
nnoremap <C-x> "+x  
vnoremap <C-x> "+x  
inoremap <C-x> <Esc>"+x  
  
" When LeftMouse click once or twice, turn into Insert Model  
"nnoremap <LeftMouse> i  
"nnoremap <2-LeftMouse> i  
  
" Appearance------------------------------------------------------------  
  
" Add line number ++++++++++++++++++++++++++++++++++++++++++++++++++++++  
set number  
  
" Add high light line and crow like a cross ++++++++++++++++++++++++++++  
set cursorline  
highlight CursorLine   cterm=NONE ctermbg=lightblue ctermfg=white guibg=lightblue guifg=white  
set cursorcolumn  
highlight CursorColumn cterm=NONE ctermbg=lightblue ctermfg=white guibg=lightblue guifg=white  
  
" Add high light syntax ++++++++++++++++++++++++  
syntax on  
  
  
  
" Other Settings--------------------------------------------------------  
  
" nocompatible with vi and using the complete model ++++++++++++++++++++  
set nocompatible  
  
" word wrap (auto linefeed) ++++++++++++++++++++++++++++++++++++++++++++  
set wrap  
  
" Show the  inputted commands on low right +++++++++++++++++++++++++++++  
set ruler  
  
" Add high light searching ++++++++++++++++++++++++++++++++++++++++++++++  
set incsearch
```