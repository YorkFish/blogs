# 4. 光标移动

### 1. 更快的上下移动

```
noremap <silent> K 5k
noremap <silent> J 5j
```

### 2. 更快的词语移动

```
noremap W 5w
noremap B 5b
```

### 3. 更快的屏幕移动

```
noremap <C-E> 5<C-e>
noremap <C-U> 5<C-y>
```

### 4. 更改 H 与 L

```
" 把 H 改为移动到行首
noremap <silent> H 0

" 把 L 改为移动到行尾
noremap <silent> L $
```

## 5. Home 与 End

```
" 插入模式下，将光标移动到行尾
inoremap <C-a> <ESC>A

" 命令模式下，将光标移动到行首
cnoremap <C-a> <Home>

" 命令模式下，将光标移动到行尾
cnoremap <C-e> <End>
```
