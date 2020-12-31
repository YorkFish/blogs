# 8. Markdown 设置

## 1. 设置常用快捷键

### 直接用

| 快捷键 | 命令原因 | 释义 |
| :---: | :--- | :--- |
| `,l` | split **<font color="red">l</font>**ine | 分割线 |
| `,t` | **<font color="red">t</font>**ask list | 任务列表 |

```
autocmd Filetype markdown inoremap <buffer> ,l ***<Enter><Enter>
autocmd Filetype markdown inoremap <buffer> ,t - [ ] 
```

!!! warning "注意"
    task list 的形式是 `- [] xxx`，`]` 后有一个空格，别忘了

### 配合使用（一）

| 快捷键 | 命令原因 | 释义 |
| :---: | :--- | :--- |
| `,m` | **<font color="red">m</font>**ark | 标记 |
| `,i` | **<font color="red">i</font>**talics | 斜体 |
| `,b` | **<font color="red">b</font>**old | 粗体 |
| `,d` | **<font color="red">d</font>**elete | 删除 |
| `,a` | `<a>` 标签 | 链接 |
| `,p` | **<font color="red">p</font>**icture | 图片 |

!!! example "以“标记”为例"
    1. 插入模式下，键入 <kbd>,</kbd> + <kbd>i</kbd>
    2. 直接写入内容，写完要标记的文字后
        - 若键入 <kbd>,</kbd> + <kbd>f</kbd>，则光标跳到后方
        - 若键入 <kbd>,</kbd> + <kbd>w</kbd>，则光标跳到下方

```
autocmd Filetype markdown inoremap <buffer> ,f <Esc>/<++><CR>:nohlsearch<CR>"_c4l
autocmd Filetype markdown inoremap <buffer> ,w <Esc>/ <++><CR>:nohlsearch<CR>"_c5l<CR>

autocmd Filetype markdown inoremap <buffer> ,m `` <++><Esc>F`i
autocmd Filetype markdown inoremap <buffer> ,i ** <++><Esc>F*i
autocmd Filetype markdown inoremap <buffer> ,b **** <++><Esc>F*hi
autocmd Filetype markdown inoremap <buffer> ,s ~~~~ <++><Esc>F~hi
autocmd Filetype markdown inoremap <buffer> ,a [](<++>) <++><Esc>F[a
autocmd Filetype markdown inoremap <buffer> ,p ![](<++>) <++><Esc>F[a
```

### 配合使用（二）

| 快捷键 | 命令原因 | 释义 |
| :---: | :--- | :--- |
| `,c` | **<font color="red">c</font>**ode | 代码块 |
| `,1` | 一级标签 | 标签，依次类推，下面设定了前四级 |

!!! note ""
    只需要搭配 `,f`

```
autocmd Filetype markdown inoremap <buffer> ,c ```<Enter><++><Enter>```<Enter><Enter><++><Esc>4kA
autocmd Filetype markdown inoremap <buffer> ,1 #<Space><Enter><++><Esc>kA
autocmd Filetype markdown inoremap <buffer> ,2 ##<Space><Enter><++><Esc>kA
autocmd Filetype markdown inoremap <buffer> ,3 ###<Space><Enter><++><Esc>kA
autocmd Filetype markdown inoremap <buffer> ,4 ####<Space><Enter><++><Esc>kA
```

!!! note
    - 新建文档 `md-snippets.vim`，并写入上方设置
    - 文档存在 `C:\Users\York\AppData\Local\nvim\`

## 2. 编辑配置文件 init.vim

```
...
source ~/AppData/Local/nvim/md-snippets.vim
autocmd BufRead,BufNewFile *.md setlocal spell
```
