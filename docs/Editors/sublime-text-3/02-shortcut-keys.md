# 2. 快捷键

## 1. 定位跳转

### Ctrl g

在当前文件中定位行数

### Ctrl [Shift] m

- <kbd>Ctrl</kbd> + <kbd>m</kbd> : 成对括号间反复跳
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>m</kbd>
    - 按一次，选中当前括号间的内容
    - 按两次，连带括号一并选中

### Ctrl [Shift] r

- <kbd>Ctrl</kbd> + <kbd>r</kbd> : 在当前文件中定位函数
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>r</kbd> : 在当前项目中定位函数

### Ctrl p

| 命令 | 释义 |
| :--- | :--- |
| `name.py`      | 查找文件 |
| `name.py:15`   | 查找文件 + 定位行数 |
| `name.py@main` | 查找文件 + 定位函数 |

### Ctrl [Shift] Enter

- <kbd>Ctrl</kbd> + <kbd>Enter</kbd> : 向下插入新行
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Enter</kbd> : 向上插入新行

### Alt [Shift] -

- 在前后编辑处跳转
- <kbd>Alt</kbd> + <kbd>-</kbd> :往前跳
- <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>-</kbd> : 往后跳

### 切换标签页

- <kbd>Ctrl</kbd> + <kbd>PgUp</kbd>
- <kbd>Ctrl</kbd> + <kbd>PgDn</kbd>
- <kbd>Ctrl</kbd> + <kbd>Tab</kbd>
- <kbd>Ctrl</kbd> + 数字

!!! note
    - 略有不同
    - `<C-Tab>` 不能在分屏间跳

## 2. 选中本行

- <kbd>Ctrl</kbd> + <kbd>l</kbd> : 选中光标所在行

## 3. 折叠展开

### 代码

- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>[</kbd> : 折叠选中的代码
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>]</kbd> : 展开被折叠代码

### 侧边栏

- <kbd>Ctrl</kbd> <kbd>k</kbd> + <kbd>Ctrl</kbd> <kbd>b</kbd>
- <kbd>Ctrl</kbd> 可以按住不放，但 <kbd>k</kbd> 和 <kbd>b</kbd> 需要先后按

## 4. 注释

- <kbd>Ctrl</kbd> + <kbd>/</kbd> : 注释本行或注释选中部分
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>/</kbd> : 注释当前 `html` 标签块

## 5. 拼写检查

- <kbd>F6</kbd>
- 或者 `View` > `Spell Check`

***

## 其他快捷键

- <kbd>Ctrl</kbd> + <kbd>d</kbd> : 批量编辑，按 <kbd>Esc</kbd> 退出
- <kbd>Ctrl</kbd> + 鼠标左键 : 同上
- <kbd>Alt</kbd> +  <kbd>F3</kbd> : 选中所有相同变量

- <kbd>Shift</kbd> + 鼠标右键 : 列选

- <kbd>Ctrl</kbd> + 方向键 : 单词间跳转
- <kbd>Ctrl</kbd> + <kbd>Home</kbd> : 跳转至文件开头
- <kbd>Ctrl</kbd> + <kbd>End</kbd> : 跳转至文件末尾
- <kbd>Ctrl</kbd> + <kbd>Backspace</kbd> : 在本“词”，删除光标之前部分
- <kbd>Ctrl</kbd> + <kbd>Delete</kbd> : 在本“词”，删除光标之后部分
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Backspace</kbd> : 在本行，删除光标之前部分
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Delete</kbd> : 在本行，删除光标之后部分

- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>a</kbd> : 选中 `html` 标签中的内容（需要光标在标签框住的词上）

- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>d</kbd> : 复制本行并粘贴至下方
- <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>k</kbd> : 删除本行

- <kbd>Ctrl</kbd> + <kbd>j</kbd> : 将下一行合并到本行末尾

- <kbd>Alt</kbd> + <kbd>Shift</kbd> + 数字 : 分屏显示

- <kbd>Shift</kbd> + <kbd>F11</kbd> : 专注编写模式

***

## 自定义快捷键

1. `Preferences` > `Key Bindings`
2. 在 `{}` 中添加

    ```json
    {
        "keys": ["ctrl+f6"],
        "command": "build",
        "args": {"variant": "Run in Sublime"}
    },
    {
        "keys": ["ctrl+f7"],
        "command": "build",
        "args": {"variant": "Run in CMD"}
    }
    ```

- 按我之后的配置
    - <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>b</kbd> : 选择 编译/运行/调试
    - <kbd>Ctrl</kbd> + <kbd>b</kbd> : 重复上回选择的结果
    - <kbd>Ctrl</kbd> + <kbd>F6</kbd> : 在 Sublime 里显示运行结果（不能交互）
    - <kbd>Ctrl</kbd> + <kbd>F7</kbd> : 弹出新窗口显示运行结果
- 优点
    1. 运行程序的快捷键通用于 `C/C++` 与 `Python`
    2. 不装插件也能交互
    3. 在 Sublime 里显示运行结果时，中文不会乱码
