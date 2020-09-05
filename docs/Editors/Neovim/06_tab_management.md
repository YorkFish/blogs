# 6. 标签页

## 1. 新建标签页

`noremap tu :tabe<CR>`

## 2. 切换标签页

```
" 切到上页
noremap tn :-tabnext<CR>

" 切到下页
noremap ti :+tabnext<CR>
```

## 3. 移动标签页

```
" 标签页前移
noremap tmn :-tabmove<CR>

" 标签页后移
noremap tmi :+tabmove<CR>
```
