# 2. New Log Item

## 1. 新建项目

1. 打开命令行，进入目标目录
2. 键入 `mkdocs new my-project`
3. 执行命令后，该目录下会多出一个名为 `my-project` 的文件夹
4. `my-project` 的结构如下

    ```
    my-project/         # The project document.
        mkdocs.yml      # The configuration file.
        docs/
            index.md    # The documentation homepage.
    ```

## 2. 启动项目

1. 在命令行进入 `my-project` 目录
2. 键入 `mkdocs serve`
3. 启动成功后会显示本地服务的地址与端口：`http://127.0.0.1:8000`
4. 将 `http://127.0.0.1:8000` 复制到浏览器打开即可
5. 此时，可以继续编辑文档
    - 更改、保存后，只要操作正确，浏览器端就会自动刷新
    - 文档多的话，刷新会变慢
