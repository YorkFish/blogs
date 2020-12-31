# 12. 插入链接

## 1. Markdown 方式

### 示例与效果

#### 方式一

- 示例
    - `[address](https://github.com/YorkFish)`
- 效果
    - [address](https://github.com/YorkFish)

#### 方式二

- 示例

    ```
    [address][01]
            
    [01]: https://github.com/YorkFish
    ```

- 效果

    [address][01]

### 加 "title"

- 示例
    - `[address](https://github.com/YorkFish "GitHub")`
- 效果
    - [address](https://github.com/YorkFish "GitHub")

## 2. HTML 方式

- 用法：借助 `HTML` 的标签 `<a>`
- 说明
    - 地址可以是“网络地址”/“本地地址”
    - 若是本地地址，可以用“绝对路径”/“相对路径”

### 示例与效果

- 示例
    - `<a href="https://github.com/YorkFish">GitHub</a>`
    - `<a href="https://github.com/YorkFish" target="_blank">GitHub</a>`
    - `<a href="https://github.com/YorkFish" target="_blank" title="GitHub">GitHub</a>`

- 效果
    - <a href="https://github.com/YorkFish">GitHub</a>
    - <a href="https://github.com/YorkFish" target="_blank">GitHub</a>
    - <a href="https://github.com/YorkFish" target="_blank" title="GitHub">GitHub</a>

[01]: https://github.com/YorkFish
