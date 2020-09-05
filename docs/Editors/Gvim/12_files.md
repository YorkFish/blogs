# 12. 合并文件与打开多个文件

## 1. 合并文件

- `:r filename` ——将 `filename` 这个文件中的所有内容复制到当前文件光标所在行之下

## 2. 打开多个文件

!!! note
    - 需要设置好环境变量
    - 有更好用的方法，具体见我在 NeoVim 中的文章
        - 《05 分屏》

1. 在命令行下进入目标目录
3. 输入 `vim -o filename1 filename2 ...`，文件垂直（上下）分布
4. 输入 `vim -O filename1 filename2 ...`，文件水平（左右）分布
5. 用 <kbd>ctrl</kbd> + <kbd>w</kbd> + 方向键，或 <kbd>ctrl</kbd> + <kbd>w</kbd> + <kbd>w</kbd>，在各文件中切换
6. 退出的两种方法
    1. 使用 `:q`, `:wq`, `:x`, `:q!`, `:wq!`, `ZZ` 中的任意一个，可以一个一个地退出
    2. 使用 `:wqa` 或 `:qa!` 可以一起退出
