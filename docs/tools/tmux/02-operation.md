## 1. 结构

- 使用 `tmux` 即可进入

```
session
    window
        pane
            shell <- here now
```

## 2. 分屏

- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>%</kbd> : 将当前 pane 左右分屏
- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>"</kbd> : 将当前 pane 上下分屏
- 按键手法类似 sublime text3 的 <kbd>Ctrl</kbd> <kbd>k</kbd> + <kbd>Ctrl</kbd> <kbd>b</kbd>
- 设定上，`%` 所在的垂线可以把键盘功能区左右分，`"` 所在的水平线可以把键盘功能区上下分
- ps: tmux 默认是 <kbd>Ctrl</kbd> <kbd>b</kbd>，这里改成了更顺手的 <kbd>Ctrl</kbd> <kbd>a</kbd>

## 3. 关闭当前的 pane

- <kbd>Ctrl</kbd> <kbd>d</kbd>
- 如果当前 window 的所有 pane 均已关闭，则自动关闭 window
- session 同理

## 4. 切换 pane

- 配置后可以用鼠标选择
- <kbd>Ctrl</kbd> <kbd>a</kbd> + 方向键/<kbd>h</kbd> <kbd>j</kbd> <kbd>k</kbd> <kbd>l</kbd>

## 5. 调整 pane 的大小

- 配置后可以用鼠标拖动分割线
- 按住 <kbd>Ctrl</kbd> <kbd>a</kbd>，用 方向键/<kbd>h</kbd> <kbd>j</kbd> <kbd>k</kbd> <kbd>l</kbd> 调整

## 6. 全屏/取消全屏

- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>z</kbd>

## 7. 挂起/打开

- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>d</kbd> : 挂起当前 session
- `tmux a`: 打开之前挂起的 session

## 8. 选择其他 session

- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>s</kbd>
    - 使用方向键或 hjkl
    - 上：选择上一项 session/window/pane
    - 下：选择下一项 session/window/pane
    - 右：展开当前项 session/window
    - 左：折叠当前项 session/window

## 9. 选择其他 window

- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>w</kbd>
- 其他同上

## 10. 创建新的 window

- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>c</kbd> : 在当前 session 中创建
- c: create

## 11. 翻阅当前 pane 内的内容

- 配置后可以用鼠标滚轮
- <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>PageUp</kbd>

## 12. 在 tmux 中选中文本

- 需要按住 <kbd>Shift</kbd>
- 支持 Windows 和 Linux，不支持 Mac

## 13. 在 tmux 中复制/粘贴文本

1. <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>[</kbd> 开始选择
2. 用鼠标选中文本，被选中的文本会被自动复制到 tmux 的剪贴板（类似 cmder）
3. <kbd>Ctrl</kbd> <kbd>a</kbd> + <kbd>]</kbd> 将剪贴板中的内容粘贴到光标处
