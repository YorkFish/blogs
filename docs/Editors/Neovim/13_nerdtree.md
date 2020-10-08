# 3. NERDTree

!!! note "nerdtree"
    - 侧边栏
    - 仓库地址：<a href="https://github.com/preservim/nerdtree" target="_blank">>>> 传送门</a>

## 1. 编辑配置文件 `init.vim`

```
call plug#begin()
Plug 'preservim/nerdtree'
call plug#end()
```

## 2. 安装完成后，左边分屏的效果

![nerdtree](.\imgs\nerdtree.png)

## 3. 配置与快捷键

### 修改配置文件 init.vim

```
" 打开/关闭
map <C-k> :NERDTreeToggle<CR>

" 修改树的显示图标
let g:NERDTreeDirArrowExpandable = '►'
let g:NERDTreeDirArrowCollapsible = '▼'
let NERDTreeAutoCenter=1

" 显示行号
let NERDTreeShowLineNumbers=1
```

!!! tip
    - 在侧边栏，用 `:q` 关闭
    - 不在侧边栏，用 `<C-k>` 关闭

### 快捷键

- <kbd>C</kbd> 设置为根
- <kbd>U</kbd> 跳到上一层
- <kbd>o</kbd> 或 <kbd>Enter</kbd> 打开/关闭文件夹，打开文件
- <kbd>c</kbd> + <kbd>d</kbd> 设置为常用工作区
- <kbd>C</kbd> + <kbd>D</kbd> 跳到常用工作区
- <kbd>m</kbd> 查看命令，<kbd>Esc</kbd> 退出

    ```
    (a)dd a childnode
    (m)ove the current node
    (d)elete the current node
    (o)pen the current node with system editor
    (c)opy the current node
    copy (p)ath to clipboard
    (l)ist the current node
    ```
