# 5. 图表

## 参考文档

`pymdown-extensions` 官方文档
    - `superfences` <a href="https://facelessuser.github.io/pymdown-extensions/extensions/superfences/" target="_blank">>>> 传送门</a>
    - `mermaid` <a href="https://facelessuser.github.io/pymdown-extensions/extras/mermaid/" target="_blank">>>> 传送门</a>

`mermaid` 官方文档：<a href="https://mermaid-js.github.io/mermaid/#/" target="_blank">>>> 传送门</a>

## flow

1. 编辑 `mkdocs.yml`

    ```
    markdown_extensions:
      - pymdownx.superfences:
          custom_fences:
            - name: flow
              class: uml-flowchart
              format: !!python/name:pymdownx.superfences.fence_code_format

    extra_javascript:
      - https://cdnjs.cloudflare.com/ajax/libs/raphael/2.3.0/raphael.min.js
      - https://cdnjs.cloudflare.com/ajax/libs/flowchart/1.12.0/flowchart.min.js
      - https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js
      - javascripts/umlconvert.js
    ```

2. 在博客根目录的 `docs` 文件夹下新建 `javascripts` 文件夹，并新建文件 `umlconvert.js`
3. 编辑 `umlconvert.js`
  - 可以参考 `pymdown-extensions` 官方文档的 `mermaid` 部分，地址在开头
  - 也可以参考<a href="https://my.oschina.net/u/3465063/blog/895151" target="_blank">这篇文章</a>

## mermaid

1. 编辑 `mkdocs.yml`

    ```
    markdown_extensions:
      - pymdownx.superfences:
          custom_fences:
            - name: mermaid
              class: mermaid
              format: !!python/name:pymdownx.superfences.fence_div_format

    extra_javascript:
      - https://cdnjs.cloudflare.com/ajax/libs/raphael/2.3.0/raphael.min.js
      - https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js
      - javascripts/umlconvert.js
    ```

2. 编辑 `umlconvert.js`
