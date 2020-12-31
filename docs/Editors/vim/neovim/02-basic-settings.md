# 2. 基本设置

!!! tips
    - 有时，`:help a-command` 会比搜索引擎更有帮助
    - 配置完成后，可以使用 `:checkhealth` 检查一下运行状况
    - 配置文件路径 `C:\Users\{username}\AppData\Local\nvim\init.vim`
    - `noremap R :source $MYVIMRC<CR>`: 修改配置文件后立即生效（没有想像的好用）

## 1. System

```
" 1. 使配色正常
let &t_ut=''
    
" 2. 将执行命令的目录改为当前文件的目录
set autochdir
```

## 2. Editor Behaviors

### 2.1 行号设置

```
" 显示行号
set number

" 高亮当前行
set cursorline

" 显示相对行号
noremap sr :set relativenumber<CR>

" 取消相对行号
noremap sn :set norelativenumber<CR>
```

!!! note "相对行号"
    - 直接用 `set relativenumber` 也行，不过我更喜欢可以开关的形式
    - 使用 `sr`, `sn` 的前提是 `s` 键失效，相关命令为 `noremap s <nop>`

### 2.2 缩进设置

```
" expandtab     用空格表示一个缩进
" noexpandtab   用制表符表示一个缩进
set expandtab

" 设置默认缩进为 4 个空格
set tabstop=4

" 设定 << 和 >> 命令移动时的宽度为 4
set shiftwidth=4

" 按 BackSpace 时可以沿着缩进(<=tabstop)删除
set softtabstop=4

" 自动缩进
set autoindent

" 默认情况下，一行输入超过 n 个字，输入空格时会造成自动换行
" textwidth 设为 0，表示禁用此功能
set textwidth=0

" 不使用表达式缩进
set indentexpr=
```

### 2.3 便于阅读

```
" 显示行尾空格
set list
set listchars=tab:\|\ ,trail:▫

" 分屏时，窗口间显示间隔
set fillchars=vert:\ ,stl:\ ,stlnc:\
    
" 上下可视行数
set scrolloff=4

" 第 80 列显示竖条
set colorcolumn=80
```

### 2.4 允许折叠

```
set foldmethod=indent
set foldlevel=99
set foldenable
```

### 2.5 命令提示

`set wildmenu`

### 2.6 拼写检查

```
" 英文拼写检查
" 启动后，在插入模式可以配合快捷键 <C-x>s
map <LEADER>sc :set spell!<CR>
```

!!! note ""
    按一次打开，再按一次关闭

### 2.7 光标位置

```
" 下次打开文件，光标停在上回结束时的位置
au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
```

### 2.8 按键检测

```
" delay=0
set ttimeoutlen=0
set notimeout
```

### 2.9 显示选项

```
" cursor      光标
" folds       折叠
" slash       转换文件路径中的 \ 为 / 以使 session 文件兼容 unix
" unix        设置 session 文件中的换行模式为 unix
set viewoptions=cursor,folds,slash,unix
```

### 2.10 画面设置

```    
" 使运行更流畅
" 加速光标的移动
set ttyfast

" 执行宏时不要重绘
set lazyredraw

" 用屏幕闪烁代替响铃
set visualbell

" 可是看作“刷新时间”
set updatetime=1000
```

### 2.11 虚拟编辑

```
" 允许可视模式的虚拟编辑
" 多行编辑时可以达到不存在的位置
set virtualedit=block
```

- 如下面那样框住
- `print(i)` 之后不存在字符，但“虚拟编辑”可以达到

    ```
         _______________
    for |i in range(10):|
        |print(i)       |
         ---------------
    ```

### 2.12 编码与格式

```
" 设置编码
set encoding=utf-8

" 设置字体
set guifont=Cascadia\ Code\ PL:h16

" t: 根据 textwidth 自动折行
" c: 在注释中自动折行，插入合适的注释起始字符
set formatoptions-=tc
```

### 2.13 搜索时的大小写

```
" 默认忽略大小写
set ignorecase

" 键入大写时，区分大小写
set smartcase
```

### 2.14 底部状态栏显示设置

```
" 左下角不显示如 "--INSERT--" 之类的状态栏
set noshowmode

" 右下角显示部分键入的命令（可视模式下还会显示一些长度）
set showcmd

" 不给出完整的菜单信息
set shortmess+=c

" 即时预览命令的效果
set inccommand=split
```
