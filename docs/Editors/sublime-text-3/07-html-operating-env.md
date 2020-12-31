# 7. HTML 运行环境

1. `Tools` > `Build System` > `New Build System...`
2. 删去默认语句，填入如下内容

    ```json
    "shell_cmd": "start ${file}",
    "selector": "text.html",
    ```

3. 保存为 `Browse.sublime-build`

!!! tip
    - 命令 `start` 是使用默认浏览器
    - 指定浏览器的话，可以把 `start` 改为相关路径
