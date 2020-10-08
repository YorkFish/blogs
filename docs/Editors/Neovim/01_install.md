# 1. 安装

!!! quote "<a href="https://neovim.io/" target="_blank">官网</a>描述"
    - Fully compatible with Vim's editing model and the Vimscript language.
    - Start with :help nvim-from-vim if you already use Vim.

!!! Abstract "摘要"
    - 主要总结 `Neovim` 在 `Win10` 下的一些配置
    - 版本：`NVIM v0.4.3`
    - 我的配置：<a href="https://github.com/YorkFish/hello-world/blob/master/005_my_vim_config/init.vim/" target="_blank">>>> 传送门</a>

## 安装方法

1. 官方下载地址：<a href="https://github.com/neovim/neovim/releases" target="_blank">>>> 传送门</a>
2. 选择合适自己的版本，比如，我选择了 `nvim-win64.zip`
3. 下载后选一个路径解压，比如，我将其解压到了 `D:\Neovim`
4. 将 `D:\Neovim\bin` 添加到“环境变量”
5. 在命令行中用 `nvim` 代替 `vim` 使用即可

### ps

- `D:\Neovim\bin` 下有一个 `nvim-qt.exe`，可以双击打开，有些像 `Gvim`
- 安装完可以用 `:checkhealth` 检查 Neovim 的安装状态
