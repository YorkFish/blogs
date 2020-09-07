# 3. Python3 运行环境

1. `Tools` > `Build System` > `New Build System...`
2. 删去默认语句，填入如下内容

    ```json
    {
        "encoding": "cp936",
        // "shell_cmd": "python -u $file",
        // "cmd": ["C:/Users/York/AppData/Local/Programs/Python/Python38/python", "-u", "$file"],
        "cmd": ["D:/anaconda3/python", "-u", "$file"],
        "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
        "selector": "source.python",

        "variants":
        [
            {
                "name": "Run in Sublime",
                "shell_cmd": "cmd /c \"python ${file_name}\""
            },
            {
                "name": "Run in CMD",
                "shell_cmd": "start cmd /c \"python ${file_name} & pause\""
            },
        ]
    }
    ```

3. 保存为 `Python3.8.sublime-build`

!!! tip "运行命令"
    - 偷懒方法：`"shell_cmd": "python -u $file",`
    - 只装了 Python：`"cmd": ["C:/Users/York/AppData/Local/Programs/Python/Python38/python", "-u", "$file"],`
    - 只装了 Anaconda：`"cmd": ["D:/anaconda3/python", "-u", "$file"],`
    - 有了 `selector`，只要 `Tools` > `Build System` > `Automatic`，不用手动选择对应语言
    - `selector` 的值是文件的 `scope`，详见 《08 Snippet》的 `Tip`
