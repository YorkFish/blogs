# 4. Mathematical Formula

## 1. MathJax

- 官网：<a href="https://www.mathjax.org/" target="_blank">>>> 传送门</a>
- 官方文档：<a href="https://docs.mathjax.org/en/latest/web/start.html" target="_blank">>>> 传送门</a>

!!! info
    - `MkDocs` 想更好地使用数学公式，需要 `MathJax` 的帮助
    - `MkDocs-Material` 一直在升级，设置方式一直在变，需要关注官方文档

## 2. 设置

1. 编辑 `mkdocs.yml`

    ```
    ...
    markdown_extensions:
      - pymdownx.arithmatex:
          generic: true
    
    extra_javascript:
      - javascripts/config.js
      - https://polyfill.io/v3/polyfill.min.js?features=es6
      - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
    ```

2. 从博客根目录，进入 `docs` 文件夹，新建 `javascripts` 文件夹，新建 `config.js` 文档
3. 写入如下语句

    ```javascripts
    window.MathJax = {
      tex: {
        inlineMath: [["\\(", "\\)"]],
        displayMath: [["\\[", "\\]"]],
        processEscapes: true,
        processEnvironments: true
      },
      options: {
        ignoreHtmlClass: ".*|",
        processHtmlClass: "arithmatex"
      }
    };
    ```

## 3. 使用

### 3.1 inline

- 示例
    - `常数：$c$`
    - `公式：$a^2 + b^2 = c^2$`
- 效果
    - 常数：$c$
    - 公式：$a^2 + b^2 = c^2$

### 3.2 block

- 示例

        $$
        \sqrt(2)
        $$

        $$
        c = \sqrt{a^2 + b^2}
        $$

- 效果

    $$
    \sqrt(2)
    $$

    $$
    c = \sqrt{a^2 + b^2}
    $$

## 4. 更多公式符号

- 搜索 `mathjax symbols` 即可
- 列举一个: <a href="https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference" target="_blank">>>> 传送门</a>
