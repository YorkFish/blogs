# 1. Vim-Plug 的使用

!!! note
    - 仓库地址：<a href="https://github.com/junegunn/vim-plug" target="_blank">>>> 传送门</a>
    - Tutorial: <a href="https://github.com/junegunn/vim-plug/wiki/tutorial" target="_blank">>>> 传送门</a>

## 1. 安装

1. 可手动将 `Vim-Plug` 仓库的 `plug.vim` 复制到 `C:\Users\{username}\AppData\Local\nvim\autoload` 文件夹下
    - 若没有 `autoload` 文件夹，自己新建一个即可
2. 在配置文件 `init.vim` 中添加如下语句

    ```
    call plug#begin('~/.vim/plugged')
    Plug '...'  " 这里填插件信息；一般，目标插件的 README 上会写
    call plug#end()
    ```

3. 打开 `nvim-qt` 或在命令行输入 `nvim`，使用命令 `:PlugInstall`

## 2. 卸载

1. 在 `init.vim` 中删除相应的语句
    - 若想卸载插件，就删除或注释相应的语句
    - 若插件有相关配置，记得删除或注释
2. 打开 `neovim`，使用命令 `:PlugClean` 即可
3. 卸载插件后可以用 `:PlugStatus` 查看当前插件的安装状态
