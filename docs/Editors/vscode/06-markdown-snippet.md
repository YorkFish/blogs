# 添加 Markdown 的 Snippets

## 1. 添加 Snippets

1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
2. 输入 `snippets`
3. 选择 `Preferences: User Snippets`
4. 输入 `markdown`
5. 选择 `markdown.json (Markdown)`
6. 编辑

    ```json
    {
        "print hugo-zdoc header": {
            "prefix": "hugodoc",
            "body": [
                "---",
                "title: \"${1:title}\"",
                "description: \"\"",
                "date: ${2:year}-${3:month}-${4:day}T00:00:00+08:00",
                "draft: false",
                "weight: ${5:weight}",
                "---",
                "",
                "$0"
            ],
            "description": "for hugo-zdoc"
        }
    }
    ```

## 2. 编辑 settings.json

- 可以修改全局的，也可以修改工作区的
- 工作区配置文件：`.vscode/settings.json`
- 全局配置文件
    1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
    2. 输入 `settings`
    3. 选择 `Preferences: Open Settings (JSON)`

### 编辑方法

- 添加如下语句

    ```json
    "[markdown]": {
        "editor.quickSuggestions": true
    }
    ```
