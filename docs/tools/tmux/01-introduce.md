## 1. 功能

1. 分屏
2. 允许断开 Terminal 连接后，继续运行进程

## 2. 结构

- 一个 tmux 可以包含多个 session
- 一个 session 可以包含多个 window
- 一个 window 可以包含多个 pane

```
tmux:
    session 0:
        window 0:
            pane 0
            pane 1
            pane 2
            ...
        window 1
        window 2
        ...
    session 1
    session 2
    ...
```
