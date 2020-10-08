# 1. 基本设置

!!! note ""
    - 英文官网：<a href="https://www.sublimetext.com/" target="_blank">>>> 传送门</a>
    - 中文官网：<a href="https://sublimetextcn.com/" target="_blank">>>> 传送门</a>
    - 中文文档：<a href="https://www.sublimetextcn.com/docs/3/index.html" target="_blank">>>> 传送门</a>
    - 社区文档：<a href="https://docs.sublimetext.io/" target="_blank">>>> 传送门</a>
    - 非官方文档：<a href="https://sublime-text-unofficial-documentation.readthedocs.io/en/latest/" target="_blank">>>> 传送门</a>

!!! info
    - 我使用的版本：3.2.2 (BUILD 3211)
    - 我使用的系统：Win10

## 1. 隐藏小地图

`view` > `Hide Minimap`

***

!!! note
    1. `Preferences` > `Key Bindings`
    2. 在右分屏的 `[]` 中添加设置即可

## 2. 代码格式化

- 本行格式化

    ```json
    {
        "keys": ["ctrl+alt+l"],
        "command": "reindent",
        "args": {"single_line": true}
    },
    ```

- 全局格式化
    
    - 把上面的 `single_line` 设为 `false` 即可

## 3. 终止死循环

- 添加如下内容

    ```json
    {
        "keys": ["ctrl+shift+c"],
        "command": "exec",
        "args": {"kill": true}
    },
    ```

## 4. 切换补全候选

- 默认快捷键是 <kbd>Ctrl</kbd> + <kbd>Space</kbd>
- 因为与输入法的“切换中英文”快捷键冲突，所以改成 <kbd>Alt</kbd> + <kbd>Space</kbd>

    ```json
    {
        "keys": ["alt+space"],
        "command": "auto_complete"
    },
    ```

***

!!! note
    1. `Preferences` > `Settings`
    2. 在右分屏的 `{}` 中添加设置即可
    3. `User` 中的语句保存后重新打开，会按照字母排序

## 5. 字体

```json
"font_face": "Cascadia Code PL",
"font_size": 18,
```

### 查看当前字体

- 快捷键：<kbd>Ctrl</kbd> + <kbd>\`</kbd>
- 命令：`view.settings().get('font_face')`

```
>>> view.settings().get('font_face')
'Cascadia Code PL'
```

## 6. 显示

```json
// 显示编码
"show_encoding": true,

// 显示换行方式
"show_line_endings": true,
```

- 显示在右下角

## 7. 高亮

```json
// 所在行高亮
"highlight_line": true,

// 80 列提示线
"rulers": [79],
```

## 8. Tab 键

```json
// Tab 键默认宽度
"tab_size": 4,

// Tab 键转空格
"translate_tabs_to_spaces": true,

// 取消 Tab 的自动补全
"tab_completion": false,
```

- 需要缩进而非补全时，按 <kbd>Shift</kbd> + <kbd>Tab</kbd>

## 9. Enter 键

```json
// 直接回车，而不是补全
"auto_complete_commit_on_tab": true,
```

## 10. 启用 Vim

### Step1

```json
"ignored_packages": [],
```

!!! note
    1. 若没有这句，加上即可
    2. 若有，注释或删除里面的 `"Vintage"`
    3. 以后装了插件，若只想暂时停用，而不卸载，可以在这里添加插件名

### Step2

```json
// 激活一部分与 Ctrl 有关的快捷键
// 激活后，它们在 Sublime 中原有的功能就没了
"vintage_ctrl_keys": true,

// 新开的文件默认是 normal 模式
// 上回未关的文件保留之前的模式
"vintage_start_in_command_mode": true,
```

!!! note
    - 装了 `Vintageous` 插件就不用添加以上语句了
    - `<C-[>` : 同 `Esc`
    - `<C-R>` : 恢复撤销
    - `<C-Y>` : 向下滚动一行
    - `<C-E>` : 向上滚动一行
    - `<C-F>` : 下一页
    - `<C-B>` : 上一页
