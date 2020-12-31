# 2. coc.nvim

!!! note "coc.nvim"
    - 补全
    - 仓库地址：<a href="https://github.com/neoclide/coc.nvim" target="_blank">>>> 传送门</a>

## 1. 编辑配置文件 `init.vim`

```
call plug#begin()
Plug 'neoclide/coc.nvim', {'branch': 'release'}
call plug#end()
```

## 2. 安装依赖

- 命令行安装 `pylint`: `pip install pylint`
- 命令行安装 `jedi`: `pip install jedi`

## 3. 一些命令

- `:help coc-nvim`: 查看帮助文档
- `:CocInfo`: 查看安装信息
- `:CocInstall xxx[, xxx]`: 安装扩展
- `:CocUninstall`: 删除扩展
- `:CocList extensions`: 列出扩展信息
    - `*` 已启用
    - `+` 已安装
    - `<C-k>`, `<C-j>` 上下选择
- `:CocConfig`: `Coc.nvim` 的配置文件，安装完 `coc-json` 后可用

## 4. 一些扩展

- `coc-json`: 必要的扩展，可以像 `VSCode` 那样配置 `vim`
- `coc-vimlsp`: 必要的扩展，语言支持
- `marketplace`: 可以帮助发现扩展

!!! tip ""
    - 若要方便在别处使用 `nvim`，可在配置文件中写入如下语句
    - `let g:coc_global_extensions = ['coc-json', 'coc-vimlsp']`

## 5. 选择格式检查工具

1. `:CocCommand python.setLinter`
2. 输入 5 并回车

## 6. 编辑配置文件 `init.vim`

### 方便跳转

```
" 允许在有未保存的修改时切换缓冲区，此时的修改由 vim 负责保存
set hidden
```

### Tab 补全

```
inoremap <silent><expr> <TAB>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()
inoremap <expr><S-TAB> pumvisible() ? "\<C-p>" : "\<C-h>"

function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction
```

### 弹出补全

`inoremap <silent><expr> <s-space> coc#refresh()`

### 跳转至报错处

```
nmap <silent> <LEADER>- <Plug>(coc-diagnostic-prev)
nmap <silent> <LEADER>+ <Plug>(coc-diagnostic-next)
```

### 跳转至定义处等

```
nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gy <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)
```

### 重命名符号

`nmap <leader>rn <Plug>(coc-rename)`

### 查看文档信息

```
nnoremap <silent> <LEADER>h :call <SID>show_documentation()<CR>

function! s:show_documentation()
  if (index(['vim','help'], &filetype) >= 0)
    execute 'h '.expand('<cword>')
  else
    call CocActionAsync('doHover')
  endif
endfunction
```
