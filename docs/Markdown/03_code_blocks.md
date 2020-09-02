# 3. 代码块

## 1. 用法

### 用法一

- 缩进 + 程序代码
    - 缩进是 `n` 个 `Tab`，一般比上一层缩进多一

### 用法二

- \`\`\` + [语言名] + 程序代码 + \`\`\`

### 用法三

- 借助 `HTML` 的标签 `<code>`
    - 需要配合换行标签 `<br>`

## 2. 说明

- 代码中有 \`\`\` 时，可以考虑方法一
- 有些符号需要转义，放到代码块中可以省去些麻烦

## 3. 示例与效果

### 用法一

- 示例

    ```
        print("Markdown")
        print('1')
        print('2')
    ```

- 效果

        print("Markdown")
        print('1')
        print('2')

### 用法二

- 示例

        ```python
        print("Markdown")
        print('1')
        print('2')
        ​```

- 效果

    ```python
    print("Markdown")
    print('1')
    print('2')
    ```

### 用法三

- 示例

    ```
    <code>
    print("Markdown") <br>
    print('1') <br>
    print('2')
    </code>
    ```
    
- 效果

    <code>
    print("Markdown") <br>
    print('1') <br>
    print('2')
    </code>
