# 7. 配色设置

## 1. 启动色彩支持

```
set termguicolors
let $NVIM_TUI_ENABLE_TRUE_COLOR=1
```

## 2. 使用 molokai 配色

!!! note "前提"
    1. 搜索 <a href="https://github.com/tomasr/molokai" target="_blank">molokai</a>
    2. 把 `molokai.vim` 拷贝到 `C:\Users\York\AppData\Local\nvim\colors`
        - 若没有 `colors` 文件夹，自己新建一个即可
    3. 另外，把 `molokai.vim` 拷贝到 `D:\Neovim\share\nvim\runtime\colors` 也行

```
colorscheme molokai
let g:molokai_original = 1
```
