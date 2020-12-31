# 13. 插入图片

## 1. 示例与效果

### 用法一

- 示例

    `![Totodile](.\imgs\Totodile.png)`

- 效果

    ![Totodile](.\imgs\Totodile.png)

### 用法二

- 示例

    ```
    ![Totodile][01]
    
    [01]: .\imgs\Totodile.png
    ```

- 效果

    ![Totodile][01]

## 2. 说明

- 第一个中括号内填名称或空着
    - 若填了，在图片没有正常显示时，会显示填写的信息
- 地址可以是“网络地址”/“本地地址”
- 若是本地地址，可以用“绝对路径”/“相对路径”

## 3. 加 "title"

- 示例

    `![Totodile](.\imgs\Totodile.png)`

- 效果

    ![Totodile](.\imgs\Totodile.png "Totodile")


## 4. 指定图片大小

- 借用 `HTML` 的标签 `<img>`
- 示例

    `<img src=".\imgs\Totodile.png" alt="PokeMMO" title="Totodile" width="250" height="200" />`

- 效果

    <img src="https://yorkfish.github.io/blogs/Markdown/imgs/Totodile.png" alt="PokeMMO" title="Totodile" width="250" height="200" />

[01]: .\imgs\Totodile.png
