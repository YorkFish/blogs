# 5. 分屏

!!! note "需要“牺牲” s"
    命令：`noremap s <nop>`

## 1. 分屏

```
" 向右分屏
set splitright

" 向下分屏
set splitbelow

" up  /down  (horizontal)
" left/right (vertical)
noremap sk :set nosplitbelow<CR>:split<CR>:set splitbelow<CR>
noremap sj :set splitbelow<CR>:split<CR>
noremap sh :set nosplitright<CR>:vsplit<CR>:set splitright<CR>
noremap sl :set splitright<CR>:vsplit<CR>
```

## 2. 调整大小

```
noremap <up> :res +5<CR>
noremap <down> :res -5<CR>
noremap <left> :vertical resize-5<CR>
noremap <right> :vertical resize+5<CR>
```

## 3. 改变排列

```
" 纵向变横向（左右变上下）
noremap sf <C-w>t<C-w>K

" 横向变纵向（上下变左右）
noremap sv <C-w>t<C-w>H
```

## 4. 切换屏幕

```
noremap <LEADER>w <C-w>w
noremap <LEADER>k <C-w>k
noremap <LEADER>j <C-w>j
noremap <LEADER>h <C-w>h
noremap <LEADER>l <C-w>l
```

## 5. 打开右屏

`noremap st :set splitright<CR>:vsplit<CR>:term<CR>3jA`

## 6. 关闭屏幕

`noremap <LEADER>q <C-w>j:q<CR>`

!!! note ""
    关闭 下边/右边

## 7. 便于阅读

```
" 横向（上下）分割的窗口间显示分割线
set fillchars=vert:\ ,stl:\ ,stlnc:\
```
