# 1. 安装并修改默认开启路径

## 1. 安装

### 方式一

- 如果安装过 <a href="https://www.anaconda.com/" target="_blank">Anaconda</a>，不必重复安装

### 方式二

- 如果只安装了官方的 <a href="https://www.python.org/" target="_blank">Python</a>，可以使用 `pip` 安装 `Jupyter Notebook`
- 官方文档：<a href="https://jupyter.readthedocs.io/en/latest/install/notebook-classic.html" target="_blank">>>> 传送门</a>
- 具体命令
    - `pip install --upgrade pip`
    - `pip install jupyter`

## 2. 修改默认开启地址

- 默认地址：`C:\Users\{username}`
- 我的地址：`C:\Users\York`

### 具体步骤

1. 打开 `CMD`，输入 `jupyter notebook --generate-config`，如下

    ```
    C:\Users\York>jupyter notebook --generate-config
    Writing default config to: C:\Users\York\.jupyter\jupyter_notebook_config.py
    ```

2. 打开 `jupyter_notebook_config.py`，搜索 `c.NotebookApp.notebook_dir`
3. 取消注释
4. `c.NotebookApp.notebook_dir = ''` -> `c.NotebookApp.notebook_dir = 'D:\\JupyterDocs'`
    - 地址改成自己喜欢的就好，但不能是不存在的路径
    - 路径中的斜杠，要么是 `/`，要么是 `\\`
5. 保存退出
6. 至此，在命令行输入 `Jupyter Notebook` 满足需求，但桌面图标与开始屏幕的图标并未生效

### 桌面图标的后续步骤

1. 右击图标，选择“属性”
    - 删除“目标”一栏中的 `'%USERPROFILE%/'`
    - 或者改成 `'D:/JupyterDocs/'`
2. 依次点击“应用”、“确定”

### 开始屏幕图标的后续步骤

1. 右击图标，依次选择“更多”、“打开文件位置”
2. 在弹出的文件夹内重复上方“桌面图标的后续步骤”即可

### ps

- 我把 `Anaconda` 装在 `D:\anaconda3`
- `Jupyter Notebook` 启动程序的路径是：`D:\anaconda3\Scripts\jupyter-notebook.exe`
- 把这个文件“发送到桌面快捷方式”或者“固定到开始屏幕”，也行
