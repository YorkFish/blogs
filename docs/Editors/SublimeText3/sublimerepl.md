# sublimeREPL

## 1. 安装

<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> > `Install Package` > `sublimeREPL`

## 2. 使用

1. 使用 <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>2</kbd> 将界面调成“双页”
2. `Tools` > `SublimeREPL` > `Python` > `Python - RUN current file`

## 3. 设置快捷键

1. `Preference` > `Key Bidings`
2. 添加如下语句

    ```json
    {
        "keys": ["alt+f5"],
        "caption": "SublimeREPL: Python - RUN current file",
        "command": "run_existing_window_command",
        "args": {
            "id": "repl_python_run",
            "file": "config/Python/Main.sublime-menu"
        }
    },
    {
        "keys":["alt+f6"],
        "caption": "SublimeREPL: Python",
        "command": "run_existing_window_command", 
        "args": {
            "id": "repl_python",
            "file": "config/Python/Main.sublime-menu"
        }
    },
    {
        "keys": ["alt+f8"],
        "caption": "SublimeREPL: Python - PDB current file",
        "command": "run_existing_window_command",
        "args": {
            "id": "repl_python_pdb",
            "file": "config/Python/Main.sublime-menu"
        }
    },
    ```

## 4. pdb 常用命令

| 命令 | 解释 |
| :--- | :--- |
| b 或 break | 设置断点 |
| c 或 continue | 继续执行程序 |
| l 或 list | 查看当前行的代码段 |
| s 或 step | 进入函数 |
| r 或 return | 执行代码直到从当前函数返回 |
| e 或 qxit | 中止并退出 |
| n 或 next | 执行下一行 |
| pp | 打印变量的值 |
| help | 帮助 |

## 5. 关于虚拟环境

!!! note ""
    使用虚拟环境中的 Python 运行 sublimeREPL

1. `Preference` > `Package Settings` > `SublimeREPL` > `Settings - User`
2. 在 `{}` 中添加虚拟环境中 `python.exe` 的路径

    ```json
    "default_extend_env": {
        "PATH": "D:/SublimeProjects/for_python/venv/Scripts"
    },
    ```
