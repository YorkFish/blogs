# 4. C 运行环境

!!! info
    我安装的 `gcc` 版本：`8.1.0 (win32)`

1. `Tools` > `Build System` > `New Build System...`
2. 删去默认语句，填入如下内容

    ```json
    {
        "encoding": "cp936",
        "working_dir": "$file_path",
        "shell_cmd": "gcc -Wall -std=c99 -fexec-charset=gbk \"$file_name\" -o \"$file_base_name\"",
        "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
        "selector": "source.c",
     
        "variants": 
        [
            {
                "name": "Run in Sublime",
                "shell_cmd": "cmd /c \"${file_path}/${file_base_name}\""
            },
            {
                "name": "Run in CMD",
                "shell_cmd": "start cmd /c \"\"${file_path}/${file_base_name}\" & pause\""
            },
            {
                "name": "gdb Debug",
                "shell_cmd": "gcc -g -std=c99 -fexec-charset=gbk \"$file\" -o \"$file_base_name\" && start cmd /c gdb ${file_path}/${file_base_name} & pause"
            }
        ]
    }
    ```

3. 保存为 `C99.sublime-build`
