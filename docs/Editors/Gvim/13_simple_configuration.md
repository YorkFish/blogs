# 13. 简洁流配置

!!! info "参数"
    - 环境：`Win10`
    - 软件版本：`gVim8.1.1`

!!! note "说明"
    - 安装目的：方便我快速地打开一些小文件
    - 配置目标：简洁，有些基本功能就行
    - 我的配置：<a href="https://github.com/YorkFish/hello-world/blob/master/005_my_vim_config/_vimrc/" target="_blank">>>> 传送门</a>

## 1. 前后效果

- 配置前

    ![](.\imgs\13-01_before_config.png)

- 配置后

    ![](.\imgs\13-02_after_config.png)

!!! note ""
    主要就是“隐藏了顶部栏目”和“更改了配色”

## 2. 编辑配置文件 \_vimrc

### 2.1 配置文件地址

- 若软件装在 `D:\Vim`，则 `_vimrc` 就在这个目录里
- 安全起见，可以先拷贝一个副本
- `Windows` 下装好软件后，`_vimrc` 里面大概率是有代码的，把新的配置添加到开头即可
- `"` 为注释符号

### 2.2 隐藏栏目

```
" 防止因为 `utf-8` 而使“菜单栏”乱码
source $VIMRUNTIME/delmemu.vim <br>
source $VIMRUNTIME/menu.vim

" 隐藏菜单栏
set guioptions-=m

" 隐藏工具栏
set guioptions-=T
```

!!! warning "注意"
    `=`, `-=` 前后不要加空格

### 2.3 语法高亮

`syntax on`

### 2.4 设置编码

`set encoding=utf-8`

### 2.5 设置字体

- `set guifont=Consolas:h16`
    - 字体样式：`Consolas`
    - 字体大小：`16` 号

#### 补充

1. `Linux` 下的设置略有不同
    - `set guifont=consolas\ 16`
    - `16` 前的空格不要省
2. 如果需要设置多个字体，可以在各个字体之间添加逗号
    - `set guifont=Consolas:h16,Courier_New:h14`
    - `Vim` 会从前往后选择字体，比如：第一款没找到，就用第二款，依次类推
3. 偷懒写法：`set guifont=*`
4. 可以对特定的文件类型使用特定的字体
    - `autocmd BufEnter *.txt set guifont=Arial:h14`
    - 上面这句意为：所有的 `txt` 文件使用 `14` 号 `Arial` 字体
5. `guifont` 的其他参数
    - `set guifont=Consolas:h16:cGB2312:qDRAFT`
    - 设置字体=字体类型:字体大小:字符集:字体质量

### 2.6 更改配色

```
" gVim 8.1.1 自带 18 种配色方案
colorsheme evening
```

### 2.7 显示行号

- `set number` 或 `set nu`

### 2.8 统一缩进

```
set tabstop=4
set shiftwidth=4
set fofttabstop=4
```

### 2.9 空格代替 Tab

`set expandtab`

### 2.10 设置快速运行快捷键

```
map <A-3> : s/^/# /<CR>
map <A-4> : s/^# //<CR>
map <F5> :!python %<CR>
map <F6> :!pycodestyle %<CR>
```

### 2.11 最终效果

![](.\imgs\13-03_show.png)

***

## 后记

- 我的要求不高，用以上配置做做算法题还算舒服
- 若要继续配，可以在 `GitHub` 上搜索大神的配置作为参考
- `NeoVim`, `SpaceVim` 等也挺火的
- 我有写 `NeoVim` 的相关文章，感兴趣的朋友可以看看

### 关于配色

- 若不满足于自带的配色方案，可以上 `GitHub` 上搜索，比如
    1. 搜索 <a href="https://github.com/tomasr/molokai" target="_blank">molokai</a>
    2. 复制 `Code`
    3. 在 `安装目录\vim81\colos` 下新建文本、粘贴 `Code`、保存为 `molokai.vim`
    4. 在 `_vimrc` 里更改配色方案：`colorscheme molokai`

### 配置汇总

```
" 1.1 防止乱码
source $VIMRUNTIME/delmenu.vim
source $VIMRUNTIME/menu.vim

" 1.2 隐藏菜单栏
set guioptions-=m

" 1.3 隐藏工具栏
set guioptions-=T

" 2.1 启动语法高亮
syntax on

" 2.2 设置编码格式
set encoding=utf-8

" 2.3 设置字体
set guifont=Consolas:h16

" 2.4 设置配色方案
colorscheme molokai

" 3.1 显示行号
set number

" 3.2 设置 Tab 键为 4 个空格
set tabstop=4

" 3.3 设定“缩进移动”的宽度为 4
set shiftwidth=4

" 3.4 退格时沿着缩进(<=tabstop)删除
set softtabstop=4

" 3.5 让空格代替 Tab
set expandtab

" 4. 设置快速运行快捷键
map <A-3> : s/^/# /<CR>
map <A-4> : s/^# //<CR>
map <F5> :!python %<CR>
map <F6> :!pycodestyle %<CR>

" 下面是原来的 Code
...
```
