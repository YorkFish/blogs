# *MkDocs-Material-Markdown* 的一些用法

!!! warning
    - 需要关注官方文档，因为随着版本升级，会陆续有些变动
    - 官网地址：<a href="https://squidfunk.github.io/mkdocs-material/getting-started/" target="_blank">>>> 传送门</a>

!!! info
    1. 我仅列举了一部分
    2. 个人认为：有多种方法的，选一到两种用着顺手的即可

## 1. 代码块

### 1.1 代码高亮

- 编辑 *mkdocs.yml*
- 添加如下内容

        markdown_extensions:
          - codehilite

### 1.2 显示行号

- 方法一：更改 *mkdocs.yml* （全局有效）

        markdown_extensions:
          - codehilite:
              linenums: true

- 方法二：在语言标识符之后添加 `linenums = 1` （局部有效）

        ``` python linenums="1"
        """ Bubble sort """
        def bubble_sort(items):
            for i in range(len(items)):
                for j in range(len(items) - 1 - i):
                    if items[j] > items[j + 1]:
                        items[j], items[j + 1] = items[j + 1], items[j]
        ```

### 1.3 代码块的三种使用方法

- 用法一：**via Markdown syntax** <small>recommended</small>

        ``` python
        import tensorflow as tf
        ```

- 效果

    ``` python
    import tensorflow as tf
    ```

<br>

- 用法二：**via Shebang**

            #!/usr/bin/python
            import tensorflow as tf

- 效果

        #!/usr/bin/python
        import tensorflow as tf

<br>

- 用法三：**via three colons**

            :::python
            import tensorflow as tf

- 效果

        :::python
        import tensorflow as tf

### 1.4 指定行高亮

- 用法

        ``` python hl_lines="3 4"
        """ Bubble sort """
        def bubble_sort(items):
            for i in range(len(items)):
                for j in range(len(items) - 1 - i):
                    if items[j] > items[j + 1]:
                        items[j], items[j + 1] = items[j + 1], items[j]
        ```
    
- 效果

    ``` python hl_lines="3 4" linenums="1"
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
    ```

### 1.5 可切换代码块

- 用法

        === "Bash"
            ``` bash
            #!/bin/bash
            
            echo "Hello world!"
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
        
        === "C#"
            ``` c#
            using System;
            
            class Program {
              static void Main(string[] args) {
                Console.WriteLine("Hello world!");
              }
            }
            ```

- 效果

=== "Bash"
    ``` bash
    #!/bin/bash
    
    echo "Hello world!"
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

=== "C#"
    ``` c#
    using System;
    
    class Program {
      static void Main(string[] args) {
        Console.WriteLine("Hello world!");
      }
    }
    ```

## 2. 引用

### 准备

- 编辑 *mkdocs.yml*

        markdown_extensions:
          - admonition
          - pymdownx.details  # 打开、收起，效果见写法四

### 操作

#### note

- 写法一

        !!! note
            这是一条 note。

- 效果

    !!! note
        这是第一条 note。

<br>

- 写法二

        !!! note "改了小标题"
            这是第二条 note。

- 效果

    !!! note "改了小标题"
        这是第二条 note。

<br>

- 写法三

        !!! note ""
            这是第三条 note。
            这条 note 没有图标。

- 效果

    !!! note ""
        这是第三条 note。
        这条 note 没有图标。

<br>

- 写法四

        ??? note "请点击右边的小箭头打开这条 note"
            这是第四条 note。

- 效果

    ??? note "请点击右边的小箭头打开这条 note"
        这是第四条 note。

#### others

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

## 3. 注脚

### 准备

- 编辑 *mkdocs.yml*

        markdown_extensions:
          - footnotes

- 写法

        跳转到页面底部的脚注1[^1]，跳转到页面底部的脚注2[^2]
        
        [^1]: 点此回去
        [^2]:
            段落需要另起一行写
            有缩进
            缩进必须是四个空格

- 效果

    跳转到页面底部的脚注1[^1]，跳转到页面底部的脚注2[^2]

## 3. *PyMdom* 推荐的配置

version: Material for MkDocs 5.1.1

    markdown_extensions:
      - pymdownx.arithmatex
      - pymdownx.betterem:
          smart_enable: all
      - pymdownx.caret
      - pymdownx.critic
      - pymdownx.details
      - pymdownx.emoji:
          emoji_index: !!python/name:materialx.emoji.twemoji
          emoji_generator: !!python/name:materialx.emoji.to_svg
      - pymdownx.inlinehilite
      - pymdownx.magiclink
      - pymdownx.mark
      - pymdownx.smartsymbols
      - pymdownx.superfences
      - pymdownx.tasklist:
          custom_checkbox: true
      - pymdownx.tabbed
      - pymdownx.tilde

## 4. 其他的功能与用法

### 4.1 下划线

- 编辑 *mkdocs.yml*

        markdown_extensions:
          - pymdownx.caret

- 写法

    `^^下划线^^`

- 效果

    ^^下划线^^

### 4.2 *emoji*

- 不写也行，加上这句，显示的图标更好看
- 编辑 *mkdocs.yml*

        markdown_extensions:
          - pymdownx.emoji:
              emoji_index: !!python/name:pymdownx.emoji.twemoji
              emoji_generator: !!python/name:pymdownx.emoji.to_svg

- 写法

    `:tada:`

- 效果

    :tada:

### 4.3 *mark*

- 编辑 *mkdocs.yml*

        markdown_extensions:
          - pymdownx.mark

- 写法

    `==mark==`

- 效果

    ==mark==

### 4.4 单行高亮

- 编辑 *mkdocs.yml*

        markdown_extensions:
          - pymdownx.inlinehilite

- 写法

    \#!py3 import pymdownx

- 效果

    `#!py3 import pymdownx`

[^1]: 点此回去
[^2]:
    段落需要另起一行写
    有缩进
    缩进必须是四个空格
