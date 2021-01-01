# 配置 Vim

## 1. 安装插件

1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>x</kbd>
2. 搜索 `Vim`
3. 点击 `Install`

## 2. 配置

!!! tip
    安装插件页面就是官方文档，按照上面写的操作就行

1. 若有 `./vscode/settings.json`，就直接打开
2. 若没有，可以自己建一个，或者使用全局的
3. 打开全局的 `settings.json` 的方法如下
    1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd>
    2. 输入 `settings.json`
    3. 点击 `Preferences: Open Settings (JSON)`
4. 根据官方文档的各种例子，添加自己想要的即可

## 3. 我的简单配置

!!! note
    - 有一些模式挺有意思的
    - 因为不是重度依赖 Vim，所以只配了保存、退出、前后移动与页面切换

```json
"vim.easymotion": false,
"vim.incsearch": true,
"vim.useSystemClipboard": true,
"vim.useCtrlKeys": true,
"vim.hlsearch": true,
"vim.statusBarColorControl": false,
"vim.leader": "<space>",
// noremap
"vim.normalModeKeyBindingsNonRecursive": [
    {
        "before": ["<leader>", "<CR>"],
        "commands": [":nohl"]
    },
    {
        "before": ["S"],
        "commands": [":w"]
    },
    {
        "before": ["Q"],
        "commands": [":q"]
    },
    {
        "before": ["H"],
        "after": ["^"]
    },
    {
        "before": ["L"],
        "after": ["$"]
    },
    {
        "before": ["E"],
        "after": ["g", "T"]
    },
    {
        "before": ["R"],
        "after": ["g", "t"]
    },
    {
        "before": [";"],
        "after": [":"]
    }
],
// norecmap
"vim.commandLineModeKeyBindingsNonRecursive": [
    {
        "before": ["S"],
        "commands": ["workbench.action.files.save"]
    }
],
// imap
"vim.insertModeKeyBindings": [
    {
        "before": ["j", "k"],  // 若因此打不出 jk制服，可以改成 jj
        "after": ["<Esc>"]
    }
],
"vim.handleKeys": {
    "<C-a>": false,
    "<C-f>": false,
    "<C-n>": false
}
```
