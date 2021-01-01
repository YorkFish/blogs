# 2. 设置 C 环境

## 1. 初次打开

1. 打开一个空文件
2. 新建 `.c` 文件后，会提示安装 `C/C++` 插件
3. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
    1. `Tasks: Configure Default Build Task`
    2. `C/C++: gcc.exe build active file`
4. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
    1. `Create a launch.json file`
    2. `C++(GDB/LLDB)`

!!! note
    - `task` > 修改 gcc/g++
    - `launch` > 编译器

## 2. launch.json

- 弹出控制台的命令

    ```json
    "externalConsole": true,
    ```

- 弹出终端的命令

    ```json
    "externalConsole": false,
    "internalConsoleOptions": "neverOpen",
    ```

## 3. 其他设置

1. 左下角“齿轮” > `Settings`
2. 选择 `User` 或 `Workspace`

### C 格式

- `Extensions` > `C/C++`
    - `C_Cpp: Clang_format_fallback Style`
    - `Visual Studio` > `{BasedOnStyle: LLVM, UseTab: Never, IndentWidth: 4}`

### C 标准

- `Extensions` > `C/C++`
    - `C_Cpp > Default: C Standard` > `c99`
