# 11. 宏与补全

## 1. 宏

!!! note ""
    “宏”的功能很强大，这里拿“多行注释”举个例子

1. 在“编辑模式”按 <kbd>q</kbd> 开始录制
2. 按 <kbd>a</kbd>，这里 `a` 作为录制动作的“寄存器”
3. 依次按下 <kbd>I</kbd> <kbd>#</kbd> <kbd>space</kbd> <kbd>Esc</kbd> <kbd>j</kbd>
4. 按 <kbd>q</kbd> 结束录制
5. 连续注释十行：`10` + <kbd>@</kbd> + <kbd>a</kbd>

## 2. 补全

### 查看帮助文档

```
:help compl-generic
:help complete
:help ins-completion 
```

### 插入模式

#### 常用

<kbd>Ctrl</kbd> + <kbd>p</kbd> : 向上查找补全例子
<kbd>Ctrl</kbd> + <kbd>n</kbd> : 向下查找补全例子

#### 拼写

- `:set spell!` ： 启动
- <kbd>Ctrl</kbd> + <kbd>x</kbd> + <kbd>s</kbd> : 弹出选项
- <kbd>Ctrl</kbd> + <kbd>p</kbd> : 向上选
- <kbd>Ctrl</kbd> + <kbd>n</kbd> : 向下选

#### 其他

- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>l</kbd> : 整行补全
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>i</kbd> : 根据头文件内关键字补全
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>n</kbd> : 根据当前文件内关键字补全
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>k</kbd> : 根据字典补全（需要有字典）
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>t</kbd> : 根据同义词字典补全
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>]</kbd> : 根据标签补全
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>o</kbd> : 根据 omni 补全
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>f</kbd> : 补全文件名（同级文件或文件名）
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>d</kbd> : 补全宏定义
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>v</kbd> : 补全 vim 命令
- <kbd>Ctrl</kbd> <kbd>x</kbd> + <kbd>Ctrl</kbd> <kbd>u</kbd> : 用户自定义补全方式

!!! tip "可以 map 一下"
    如 `inoremap <C-]> <C-X><C-l>`

### 命令模式

1. 输入前缀，按上下键，可以根据历史记录“过滤补全”
2. 输入前缀，按 <kbd>Tab</kbd> 或 `<C-d>` 可以显示备选项，再按 <kbd>Tab</kbd> 进行选择

#### ps

1. <kbd>Shift</kbd> 或 <kbd>Ctrl</kbd> 配合左右键可以单词键跳转
2. 在命令模式下将进入命令模式前光标处的单词粘贴到命令行
    - <kbd>Ctrl</kbd> <kbd>r</kbd> + <kbd>Ctrl</kbd> <kbd>w</kbd> 或
    - <kbd>Ctrl</kbd> <kbd>r</kbd> + <kbd>Ctrl</kbd> <kbd>a</kbd>
3. 将当前文件名粘贴到命令行
    - <kbd>Ctrl</kbd> + <kbd>r</kbd> + <kbd>%</kbd>
4. 编辑模式下打开命令行窗口
    - `q:` : 查找命令历史记录
    - `q/` : 向前查找搜索历史记录
    - `q?` : 向后查找搜索历史记录
5. 命令模式下打开命令行窗口
    - <kbd>Ctrl</kbd> + <kbd>f</kbd>
    - `:set cedit` : 更改此快捷键
