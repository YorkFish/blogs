# 6. makefile

1. `Tools` > `Build System` > `New Build System...`
2. 删去默认语句，填入如下内容

    ```json
    {
        "encoding": "cp936",
        "shell_cmd": "mingw32-make",
        "file_regex": "^(..[^:\n]*):([0-9]+):?([0-9]+)?:? (.*)$",
        "working_dir": "${folder:${project_path:${file_path}}}",
        "selector": "source.makefile",
        "syntax": "Packages/Makefile/Make Output.sublime-syntax",
        "keyfiles": ["Makefile", "makefile"],
     
        "variants":
        [
            {
                "name": "Clean",
                "shell_cmd": "mingw32-make clean"
            },
            {
                "name": "Run in Sublime",
                "shell_cmd": "cmd /c \"${file_path}/${file_base_name}\""
            },
            {
                "name": "Run in CMD",
                "shell_cmd": "mingw32-make run"
            },
        ]
    }
    ```

3. 保存为 `mingw32-make.sublime-build`
4. `makefile` 可以这样写（缩进必须是 Tab）

    ```
    main: main.cpp Student.h Student.cpp
    	g++ -Wall -std=c++11 -fexec-charset=gbk main.cpp Student.cpp -o main
    
    clean:
    	del main.exe *.o
    
    run:
    	mingw32-make && start cmd /c "main.exe & pause"
    ```
