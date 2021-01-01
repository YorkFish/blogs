# 更改 Terminal 样式

## 方式一

1. <kbd>Ctrl</kbd> + <kbd>,</kbd>
2. 搜索 `shell`
3. 找到 `Terminal` > `Intergrated` > `Shell: Windows`
4. 页面跳转后，加入 `git-bash` 的路径

    ```json
    // 如，我把 Git 装在 D:\Git
    "terminal.integrated.shell.windows": "D:\\Git\\bin\\bash.exe",
    ```

## 方式二

- 直接打开 `.vscode\settings.json`
- 添加 `"terminal.integrated.shell.windows": "D:\\Git\\bin\\bash.exe",`

!!! bug "说明"
    - 更改了样式，有些命令会失效
    - 如，可能无法使用 pip 安装 Python 的包
    - 这时可以改回 CMD 或使用其他样式
