# 4. 表情符号 & 任务列表

## 1. 编辑 mkdocs.yml

```
markdown_extensions:
  - pymdownx.emoji:
      emoji_index: !!python/name:materialx.emoji.twemoji
      emoji_generator: !!python/name:materialx.emoji.to_svg
  - pymdownx.tasklist:
      custom_checkbox: true
```

## 2. 表情符号

- 默认写法与 `Markdown` 一致，`Material` 还有扩展，我这儿偷懒略了
- 写法

    `:tada:`

- 效果
    
    :tada:

## 3. 任务列表

- 默认写法与 `Markdown` 一致，`Material` 还有扩展，我这儿偷懒略了
- 写法

    `- [ ] 未完成`  
    `- [x] 已完成`

- 效果
    
    - [ ] 未完成
    - [x] 已完成
