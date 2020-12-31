# 4. 光标移动

### 1. 更快的上下移动

```
noremap <silent> J 5j
```

!!! note ""
    K: 查看光标处词语的帮助文档

### 2. 更快的词语移动

```
noremap W 5w
noremap B 5b
```

### 3. 更快的屏幕移动

```
noremap <C-e> 5<C-e>
noremap <C-y> 5<C-y>
```

### 4. 更改 H 与 L

```
" 把 H 改为移动到行首
noremap <silent> H 0

" 把 L 改为移动到行尾
noremap <silent> L $
```

## 5. End

```
" 插入模式下，将光标移动到行尾
inoremap <C-a> <ESC>A
```
