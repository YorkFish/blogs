# 3. 基本映射

## 1. LEADER

```
" 将空格键设为 <LEADER>
let mapleader=" "
```

## 2. 快速打开配置文件

`noremap <LEADER>rc :e ~/AppData/Local/nvim/init.vim<CR>`

## 3. 将分号映射为冒号

`noremap ; :`

!!! note ""
    冒号还是冒号

## 4. 用空格替换制表符

```
nnoremap <LEADER>tt :%s/    /\t/g
vnoremap <LEADER>tt :s/    /\t/g
```

## 5. 复制

- 往后复制

    ```
    " 普通模式下，按 Y 复制到本行结尾
    nnoremap Y y$
    ```

- 接通系统剪贴板

    ```
    " 可视模式下，将选中的文本块复制至系统剪贴板
    vnoremap Y "+y
    
    " 普通模式下，将系统剪贴板内容粘贴至 neovim
    nnoremap <Leader>p "+p
    ```

## 6. 缩进

```
nnoremap < <<
nnoremap > >>
```

!!! note ""
    原来要按两次，现在一次就行了

## 7. 高亮

```
" 开机执行 “取消搜索高亮”
exec "nohlsearch"

" 快速取消搜索后的高亮
noremap <LEADER><CR> :nohlsearch<CR>

" 高亮周围有重复的 词语/变量
noremap <LEADER>dw /\(\<\w\+\>\)\_s*\1
```

## 8. 折叠

`noremap <silent> <LEADER>o za`


## 9. 退出、全部退出与保存

```
noremap Q :q<CR>
noremap <C-q> :qa<CR>
noremap S :w<CR>
```
