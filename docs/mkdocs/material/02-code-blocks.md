# 2. 代码块

## 1. 编辑 mkdocs.yml

```
markdown_extensions:
  - pymdownx.highlight:
      use_pygments: true
      linenums: true
      linenums_style: pymdownx.inline
  - pymdownx.inlinehilite
  - pymdownx.superfences
  - pymdownx.tabbed
```

## 2. 指定行高亮

- 用法

        ``` python hl_lines="2 3"
        def bubble_sort(items):
            for i in range(len(items) - 1):
                for j in range(len(items) - 1 - i):
                    if items[j + 1] < items[j]:
                        items[j + 1], items[j] = items[j], items[j + 1]
        ```
    
- 效果

    ``` python hl_lines="2 3"
    def bubble_sort(items):
        for i in range(len(items) - 1):
            for j in range(len(items) - 1 - i):
                if items[j + 1] < items[j]:
                    items[j + 1], items[j] = items[j], items[j + 1]
    ```

## 3. 行间代码高亮

- 用法

        在语句中插入 `#!python for c in "InlineHilite": break` 高亮的代码

- 效果

    在语句中插入 `#!python for c in "InlineHilite": break` 高亮的代码

## 4. 分组代码块

- 用法

    ```       
    === "C"
    
        ``` c
        #include <stdio.h>
        
        int main(void) {
            printf("Hello world!\n");
            return 0;
        }
        ```
    
    === "C++"

        ``` c++
        #include <iostream>
        
        int main(void) {
            std::cout << "Hello world!" << std::endl;
            return 0;
        }
        ```
    ```

- 效果

    === "C"

        ``` c
        #include <stdio.h>
        
        int main(void) {
          printf("Hello world!\n");
          return 0;
        }
        ```
    
    === "C++"
    
        ``` c++
        #include <iostream>
        
        int main(void) {
          std::cout << "Hello world!" << std::endl;
          return 0;
        }
        ```

## 5. 修改颜色主题

- MkDocs 可以较方便地借助 `highlight.js` 修改代码块高亮配色
    - <a href="https://www.mkdocs.org/user-guide/styling-your-docs/#built-in-themes" target="_blank">>>> 传送门</a>
- MkDocs-Material 目前没有那么方便
