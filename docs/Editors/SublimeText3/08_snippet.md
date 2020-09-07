# 8. Snippet

1. `Tools` > `Developer` > `New Snippet...`
2. `content` 标签中的默认内容如下

    ```html
    <content><![CDATA[
    Hello, ${1:this} is a ${2:snippet}.
    ]]></content>
    ```

3. 修改为

    ```html
    <content><![CDATA[
    ---
    title: ${1:title}
    date: ${2:date}
    categories:
    tags:
    ---

    ${3}

    ]]></content>
    ```

4. 取消下方的 `tabTrigger` 标签与 `scope` 标签的注释
5. 按需编辑，如

    ```html
    <tabTrigger>hexo</tabTrigger>
    <scope>text.html.markdown</scope>
    ```

4. 保存为 `hexo-header.sublime-snippet`

!!! tip
    - `tabTrigger` 是触发词
    - 查看 `scope` 的快捷键：<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
    - 若有多个 `scope`，写在同一个标签里，用 `,` 隔开即可；不写的话，是“通配”
    - 若设置了 `${}`，按 <kbd>Tab</kbd> 即可跳转
