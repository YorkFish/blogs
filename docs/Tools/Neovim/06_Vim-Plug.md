# 使用 Vim-Plug 安装、删除插件

## 1. GitHub 上的地址

- <a href="https://github.com/junegunn/vim-plug" target="_blank">>>> 传送门</a>

## 2. 安装方法

1. 官网上说添加如下 *code* 到 **PowerShell** 上

    ```
    md ~\vimfiles\autoload
    $uri = 'https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
    (New-Object Net.WebClient).DownloadFile(
      $uri,
      $ExecutionContext.SessionState.Path.GetUnresolvedProviderPathFromPSPath(
        "~\vimfiles\autoload\plug.vim"
      )
    )
    ```

2. 上一步不行的话，可心手动将 `Vim-Plug` 仓库的 `plug.vim` 复制到 `C:\Users\YourName\AppData\Local\nvim\autoload` 文件夹下
    
    - 若没有 `autoload` 文件夹，可自行创建
4. 在配置文件 `init.vim` 中添加如下 code

        call plug#begin('~/.vim/plugged')
        Plug '...'  " 这里填插件信息，一般，目标插件的 README 上会写
        call plug#end()

5. 在命令行打开 `init.vim`，使用命令 `:PlugInstall`

### 示例

1. 比如，安装 `vim-airline` （底部状态栏），配置文件这样写

        call plug#begin('~/.vim/plugged')
        Plug 'vim-airline/vim-airline'
        call plug#end()

2. 安装完成后，左边分屏大概是这样的

    ![vim-airline](.\imgs\airline.png)

## 3. 删除方法

1. 在 `init.vim` 中删除相应的语句
    - 比如，想删 `vim-airline`，就删除 `Plug 'vim-airline/vim-airline'`
2. 在命令行打开 `init.vim`，使用命令 `:PlugClean` 即可删除
3. 删除后可以用 `:PlugStatus` 查看当前的插件情况
