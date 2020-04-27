# *Hexo*

## 1. 创建远程仓库

- 仓库名：`your-name.github.io`

## 2. 配置 *Git* + 添加 *SSH Keys*

### 2.1 设置

1. `york$ git config --global user.name "your-name"`
2. `york$ git config --global user.email "your@email.com"`

### 2.2 查看

- `york$ git config --global user.name`
- `york$ git config --global user.email`

### 2.3 连接并检验

1. `york$ ssh-keygen -t rsa -C "your@email.com"`
2. `york$ ssh -T git@github.com`

## 3. *Hexo* 的简单使用

### 3.1 安装

1. 打开 *CMD*
2. `york$ npm install -g hexo`

### 3.2 初始化

1. 新建一个文件夹
2. 右键 -> *Git Bash Here*
3. `york$ hexo init`
4. `york$ npm install hexo-deployer -- save`
5. `york$ hexo server`
    - `http://localhost:4000`

### 3.3 修改 *\_config.yml*

- 打开文件，并拉倒最下方

        ...
        # Deployment
        ## Docs: https://hexo.io/docs/deployment.html
        deploy:
          type:

- 修改后

        ...
        # Deployment
        ## Docs: https://hexo.io/docs/deployment.html
        deploy:
          type: git
          repository: git@github.com:your-name/your-name.github.io.git
          branch: master

### 3.4 生成静态文件

1. `york$ Ctrl + c`
2. `york$ hexo generate`
3. `york$ server`

## 4. 修改主题

1. 先去官网寻找主题
    - 传送门：<a href="https://hexo.io/themes/" target="_blank">>>> hexo.io</a>
    - *NextT* 值得一试
    
2. 点击主题后，页面会跳转至其 *github* 仓库

3. 下载并解压（可以改个短一点的名字，比如我用 `nexT` 命名）

4. 将上述文件夹复制到博客文件夹的 `themes` 目录下

5. 修改 *\_config.yml*

        ...
        # Extensions
        ## Plugins: https://hexo.io/plugins/
        ## Themes: https://hexo.io/themes/
        theme: landscape
        ...

6. 修改后

        ...
        # Extensions
        ## Plugins: https://hexo.io/plugins/
        ## Themes: https://hexo.io/themes/
        theme: NexT
        ...

7. `york$ hexo generate`

8. `york$ hexo server`

    - `http://localhost:4000`

## 5. 部署

- 在本地预览，没问题后部署至远程
- `york$ Ctrl + c`
- `york$ hexo deploy`
- 在浏览器中输入自己的博客地址即可查看
    - `https://your-name.github.io`
