# SublimeGDB

## 1. 安装

1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> > `Install Package` > `SubliemGDB`
2. 重启

## 2. 配置

1. `Preferneces` > `Package Settings` > `SublimeGDB` > `Settings` – `User`
2. 在 `{}` 中添加

    ```json
     "workingdir" : "${folder:${file}}",
     "commandline" : "g++ -g ${file} -o ${file_base_name} && gdb --interpreter=mi --args ./${file_base_name}",
    ```

## 3. 使用

1. 光标置于某一行，按 <kbd>F9</kbd> 键，会加入一个断点
2. 设置好断点后，按 <kbd>F5</kbd> 键启动调试

## 4. 默认快捷键

| 按键 | 功能 |
| :---: | :--- |
| <kbd>F5</kbd> | 开始调试 |
| <kbd>Ctrl</kbd> + <kbd>F5</kbd> | 停止调试 |
| <kbd>F9</kbd> | 设置断点 |
| <kbd>F10</kbd> | Step over，执行一步，不进入函数 |
| <kbd>F11</kbd> | Step into，进入函数 |
| <kbd>Shift</kbd> + <kbd>F11</kbd> | Step out，跳出函数 |

!!! tip
    可以在 `Default(windows).sublime-keymap` 修改快捷键
