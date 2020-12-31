# 3. 编辑配置文件

- `mkdocs.yml` 就是配置文件

## 1. 更换站点名称

- `site_name: My Docs` -> `site_name: YorkFish's blog`

## 2. 更换主题

### 2.1 主题简介

- MkDocs 列出的主题：<a href="https://github.com/mkdocs/mkdocs/wiki/MkDocs-Themes" target="_blank">>>> 传送门</a>
- MkDocs-Material 官方文档：<a href="https://squidfunk.github.io/mkdocs-material" target="_blank">>>> 传送门</a>

!!! info
    Mmaterial 一直在更新升级、需要经常关注

### 2.2 安装主题

- `york$ pip install mkdocs-material`
    - 若电脑中同时拥有 `Python2` 与 `Python3`，需要使用 `pip3`
    - 若系统有权限提醒，需要使用 `sudo`

### 2.3 更换主题

- 编辑 `mkdocs.yml`

    ```
    theme:
      name: material
      language: zh
      features:
        - tabs
    ```

## 3. 增加页面

### 3.1 普通页面

- 新建文档后的文件结构

    ```
    my-project/
        docs/
            01-my-first-blog.md
            about.md
            index.md
        mkdocs.yml
    ```

- 编辑 `mkdocs.yml`

    ```
    ...
    nav:
      - "index": index.md
      - "article": 01-my-first-blog.md
      - "about": about.md
    ```

- 解释
    - `Material 5.x` 推荐使用 `nav`，而不再是`pages`
    - `#` 可以用来注释
    - 缩进可以改成 4 格
    - 上方的 `article` 是导航栏上的名称
        - 双引号可以去掉
        - 用单引号也行
        - 一般在路径中有空格时加

### 3.2 折叠页面

- 文件结构

    ```
    my-project/
        docs/
            article/
                01-my-first-blog.md
                02-my-second-blog.md
                03-my-third-blog.md
            about.md
            index.md
        mkdocs.yml
    ```

- 编辑 `mkdocs.yml`

    ```
    nav:
      - index: index.md
      - article:  # 不一定要用 article，也可以是 blogs，下面的路径能对上就行
        - blog1: article/01-my-first-blog.md
        - blog2: article/02-my-second-blog.md
        - blog3: article/03-my-third-blog.md
      - about: about.md
    ```
