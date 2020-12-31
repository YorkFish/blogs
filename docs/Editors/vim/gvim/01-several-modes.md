# 1. 几种模式

!!! info
    - 主要总结 **vim** 的一些概念、配置与用法
    - 载体：**Win10, Gvim8**

!!! note
    注意光标与左下角

## 1. 插入模式

![](.\imgs\01-01_vim_insert_mode.png)

## 2. 命令模式

![](.\imgs\01-02_vim_command_mode.png)

## 3. 编辑模式（普通模式）

![](.\imgs\01-03_vim_edit_mode.png)

## 4. 可视模式

- <kbd>v</kbd> : 类似选中
- <kbd>Ctrl</kbd> + <kbd>v</kbd> : 列选择
- <kbd>Shift</kbd> + <kbd>v</kbd> : 行选择

## 5. 选择模式

- <kbd>g</kbd> + <kbd>h</kbd> : 以当前字符进入
- <kbd>g</kbd> + <kbd>H</kbd> : 以当前行进入
- <kbd>Ctrl</kbd> + <kbd>g</kbd> : 配合可视模式进入

- 进入后输入字符
    1. 进入插入模式
    2. 覆盖选中部分

## 6. 插入-普通模式

- 在插入模式下按 <kbd>Ctrl</kbd> + <kbd>o</kbd> 进入
- 此模式下可以输入一次命令，执行完这个命令会回到插入模式

!!! tip "小技巧"
    - 在插入模式下进入“插入-普通模式”
    - 按 <kbd>z</kbd> <kbd>t</kbd> 可以快速将屏幕上移
