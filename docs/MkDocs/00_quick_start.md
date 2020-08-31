# Quick Start

## 1. 初始化

1. 新建站点
    - `D:\blog>mkdocs new mysite`
2. 启动服务
    
    ```
    D:\blog>cd mysite
    D:\blog\mysite>mkdocs serve
    ```

3. 打开浏览器
    - `http://127.0.0.1:8000`
3. 结束服务
    - 在命令行使用 <kbd>Ctrl</kbd> + <kbd>c</kbd>

## 2. 增加页面

### 2.1 默认结构

```
mysite/           # The project document.
    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
```

### 2.2 新建文档

- 可以直接在文件夹 `docs` 下新建文档
- 也可以在文件夹 `docs` 下新建文件夹，然后在新文件夹下新增文档
- 想要文档被索引到，需要编辑 `mkdocs.yml`

    ```
    site_name: YorkFish
    nav:
      - "index": index.md
      - "about": about.md
      - "new":
        - "test1": new/test1.md
        - "test2": new/test2.md
        ...
    ```

## 3. 更换主题

### 3.1 readthedocs

- `readthedocs` 是自带的
- 编辑 `mkdocs.yml`

    ```
    ...
    theme: readthedocs
    ```

### 3.2 material


- `material` 需要另行安装
    - 安装命令 `york$ pip install mkdocs-material`
- 编辑 `mkdocs.yml`

    ```
    ...
    theme:
      name: material
    ```

## 4. 部署

### 4.1 几种方式

- Gitee Pages
- GitHub Pages
- Netlify
- 购买的域名
- 自己搭的服务器
- ...

### 4.2 简介一种方式

#### 4.2.1 Netlify

- 原名：`BitBalloon`
- 地址：`https://app.netlify.com`

#### 4.2.2 操作方法

1. 生成静态网页
    - 在博客根目录下使用命令：`mkdocs build`
    - 根目录下会新增文件夹 `site`
2. 打包
    - 将 `site` 文件夹打包成 `site.zip`
3. 上传
    - 登录 `Netlify`
    - 将 `site.zip` 拖到 `Drag & drop a new site`
    - 生成地址后，若想更改地址，可点击 `Edit Name`
