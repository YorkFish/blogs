# 1. 提示框

## 1. 编辑 mkdocs.yml

```
markdown_extensions:
  - admonition
  - pymdownx.details
  - pymdownx.superfences
```

## 2. 四种形式

- 以 `note` 为例

### 2.1 形式一

- 写法

    ```
    !!! note
        这是一条 note。
    ```

- 效果

    !!! note
        这是第一条 note。

### 2.2 形式二

- 写法

    ```
    !!! note "改了小标题"
        这是第二条 note。
    ```

- 效果

    !!! note "改了小标题"
        这是第二条 note。

### 2.3 形式三

- 写法

    ```
    !!! note ""
        - 这是第三条 note。
        - 这条 note 没有图标。
    ```

- 效果

    !!! note ""
        - 这是第三条 note。
        - 这条 note 没有图标。

### 2.4 形式四

- 写法

    ```
    ??? note "请点击右边的小箭头打开这条 note"
        这是第四条 note。
    ```

- 效果

    ??? note "请点击右边的小箭头打开这条 note"
        这是第四条 note。

## 3. Others

!!! abstract
    `!!! abstract`

!!! info
    `!!! info`

!!! tip
    `!!! tip`

!!! success
    `!!! success`

!!! question
    `!!! question`

!!! warning
    `!!! warning`

!!! failure
    `!!! failure`

!!! danger
    `!!! danger`

!!! bug
    `!!! bug`

!!! example
    `!!! example`

!!! quote
    `!!! quote`

- 还可以自定义
