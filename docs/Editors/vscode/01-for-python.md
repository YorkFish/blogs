# 1. 设置 Python 环境

## 1. 初次打开

1. 右侧 `Customize` > `Tools and languages` > `Python`
    - 右下角会有“自动重新载入”的提示，点击即可
2. `Customize` > `Settings and keybindings` > `Vim`
    - 右下角会有“自动重新载入”的提示，点击即可
3. 如有需要，可安装中文插件
    1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
    2. 键入 `language`
    3. 选择 `Configure Display Language` > `Install additional languages...`

## 2. 简单设置

1. 从左上角开始 `File` > `Open Folder...` > 打开一个空文件夹
2. 点击右下角的“齿轮” > `Settings`
3. 选择 `User` 或 `Workspace`

### 字体

- `Text Editor` > `Font`
    - `Font Family` > `Cascadia Code PL`
    - `Font Ligatures` > 进入 `setting.json` > `"editor.fontLigatures": true`
    - `Font Size` > `18`

### 小地图

- `Minimap` > `Enabled` > 取消对勾

### 导航路径

- `Workbench` > `Breadcrumbs` > `Enabled` > 取消对勾

### 主题

- `Workbench` > `Appearance` > `Color Theme` > `Monokai`

## 3. 虚拟环境

!!! tip
    - `Windows PowerShell` 默认无法激活“虚拟环境”，需要另外设置
    - 可以先将终端换成 `CMD`

1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
2. `Terminal: Select Default Shell` > `Command Prompt C:\Windows\System32\cmd.exe`
3. `york$ python -m venv env`
4. 点击左下角 `Python...('base': conda)`
5. 选择 `Python...('env': venv)`

## 4. pytest

1. <kbd>Ctrl</kbd> + <kbd>,</kbd>
2. 搜索 `test`
3. `Extensions` > `Python`
4. 在右侧找到 `Python > Testing: Python Enabled`，并勾选
5. 若是使用虚拟环境，则需安装 `pytest`，右会自动跳出来，自己 `pip install` 也行

## 5. Snippets

1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
2. `Preferences: Configure User Snippets`

## 6. 有用的功能

1. 右键 > `Go to Definition`
    - 可以转到模块函数的定义处
    - 可以转到自己的变量定义处
2. `Rename Symbol` : 全局替换
3. <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>f</kbd> : 代码自动整理
4. 选中 > 右键 > `Run Selection/Line in Python Terminal`

## 7. 好用的插件

- AREPL for python
- Jupyter
- Python Docstring Generator
