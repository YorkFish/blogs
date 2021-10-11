# 9. Plugin

!!! note ""
    以“添加时间”为例

1. `Tools` > `Developer` > `New Plugin...`
2. 删除默认代码，填入如下代码

    ```python
    from datetime import datetime
    from sublime_plugin import TextCommand


    class AddCurrentTimeCommand(TextCommand):
        def run(self, edit):
            t = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
            d = {"contents": t}
            self.view.run_command("insert_snippet", d)
    ```

3. 保存为 `addCurrentTime.py`
4. `Preferences` > `Key Bindings`
5. 添加如下语句

    ```json
    {
        "keys": ["alt+t"],
        "command": "add_current_time"
    },
    ```

6. 保存、退出

!!! note
    - 如此，可在任意处按 <kbd>Alt</kbd> + <kbd>t</kbd> 打印时间
    - 写 `YAML` 题头时挺有用的
    - 上一篇 `snippet` 的第三行可以改成 `title: ${1:alt+t}`
