# 6. 复制与粘贴

## 编辑模式

!!! info
    - 默认情况下，Vim 的剪贴板不与系统共用
    - 可以设置，具体见我在 NeoVim 中的文章
        - 《03 基本映射》 -> “5. 复制” -> “接通系统剪贴板”

| 命令 | 释义 |
| :---: | :--- |
| **yy** | 复制当前行 |
| **p** | 将剪贴板中的内容粘贴至 本行之下/光标之后 |
| **P** | 将剪贴板中的内容粘贴至 本行之上/光标之前 |

!!! tip
    - `y`
        - 可以与 `b`, `e`, `w` 这类命令搭配
        - 也可以配合 `v` 命令使用
    - `p/P`
        - 若剪贴板中的内容不足一行，则在行内操作
        - 若剪贴板中的内容大于等于一行，则在行外操作

!!! note ""
    本行：粗光标所在行

## 插入模式

- <kbd>Ctrl</kbd> + <kbd>y</kbd> : 复制上一行的相同列的字符，并向后粘贴
- <kbd>Ctrl</kbd> + <kbd>e</kbd> : 复制下一行的相同列的字符，并向后粘贴
