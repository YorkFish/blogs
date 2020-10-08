# 12. 映射

!!! info
    - `:help map` 可以查看相关帮助信息
    - `map` 可以映射得很复杂
        - 基本格式是：`:map 快捷键 命令`
        - 若要写入配置文件 `_vimrc`，需去掉开头的“冒号”

## 例1

- `:map <A-3> :s/^/# /<CR>` —— <kbd>Alt</kbd> + <kbd>3</kbd> : 单行注释
- `:map <A-4> :s/^# //<CR>` —— <kbd>Alt</kbd> + <kbd>4</kbd> : 取消单行注释

## 例2

- `:map <F5> :!python %<CR>` —— <kbd>F5</kbd> : 运行当前的 `.py` 文件
    - `:!` 后面可以加 `Shell` 命令

## ps
    
- `map` 有多种形式，如
    1. `noremap`
    2. `inoremap`
    3. `nnoremap`
    4. `vnoremap`
- `nore`: `no recursive`
- 以 `i`, `n`, `v` 开头，表示只在对应的模式生效
