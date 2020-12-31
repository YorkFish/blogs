# 9. 一键执行

!!! note ""
    快捷键：<kbd>m</kbd>

## 1. 基本格式

```bash
noremap m :call CompileRun()<CR>
func! CompileRun()
    exec "w"
    if &filetype == 'c'
        exec "..."
    elseif &filetype == 'cpp' || &filetype == 'cc'
        exec "..."
    endif
endfunc
```

## 2. 三种方法

### 方法一

```bash
noremap m :call CompileRun()<CR>
func! CompileRun()
    exec "w"
    if &filetype == 'c'
        exec "!gcc -Wall -finput-charset=utf-8 -fexec-charset=gbk % -o %<"
        exec "!%<"
    endif
endfunc
```

!!! warning "缺点"
    无法交互

### 方法二

```bash
noremap m :call CompileRun()<CR>
func! CompileRun()
    exec "w"
    if &filetype == 'c'
        exec "!gcc -Wall -finput-charset=utf-8 -fexec-charset=gbk % -o %<"
        :!start cmd /c "%< & pause"
    endif
endfunc
```

!!! success "效果"
    弹出一个新的命令窗口，可以交互

### 方法三

```bash
noremap m :call CompileRun()<CR>
func! CompileRun()
    exec "w"
    if &filetype == 'python'
        :sp
        :term python %
    endif
endfunc
```

!!! success "效果"
    - 向下分屏，可以交互
    - 如有需要，可以调整大小 `:res -15`
    - 若有交互，需要按 <kbd>A</kbd>
