# 5. Deploy to the Cloud

## 1. 第三方服务器

- 阿里云
- 新浪云
- Gitee
- GitHub
- Netlify
- ...

## 2. 借助 GitHub Pages

### 2.1 远程部分

1. 登录 `GitHub`
2. 新建仓库
    - 仓库名：`{username}.github.io`，配置文件中：`site_url=https://yorkfish.github.io`
    - 仓库名：`{a-world}`，配置文件中：`site_url=https://yorkfish.github.io/blogs`
3. 点击 `settings`
4. 下拉，找到 `GitHub Pages`
6. 选择 `gh-pages` -> `/(root)`，点击 `Save`

### 2.2 本地部分

1. 用 `Git Bash` 把文档上传到远程仓库
2. 在命令行（博客根目录）使用 `mkdocs gh-deploy`
    - 命令作用：生成/更新 `site`，并推送到对应的远程仓库

### 2.3 原理

1. 在本地生成一个 `site` 文件夹，里面是生成的静态网站
2. 将其推到对应的 `gh-pages` 分支
3. 通过 `GitHub Pages` 启动服务，生成目标网页

## 3. 借助 Netlify

### 3.1 打包

1. 确保关闭本地服务
2. 使用命令 `mkdocs build [--clean]`，然后博客根目录会新增一个 `site` 文件夹
3. 将 `site` 文件夹压缩为 `site.zip`

### 3.2 部署

1. 官网：<a href="https://app.netlify.com/drop" target="_blank">>>> 传送门</a>
2. 将 `site.zip` 拖到 `Drag & drop a new site`
3. 等待一段时间，网页跳转，生成地址
4. 点击 `Edit Name` 可改地址名，不过后缀是固定的
