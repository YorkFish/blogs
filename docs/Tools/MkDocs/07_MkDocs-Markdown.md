# *MkDocs-Markdown* 的一些用法

## 1. 代码块

### 例1 代码高亮

- 编辑 *mkdocs.yml*
- 添加如下内容

```
markdown_extensions:
    - codehilite
```

### 例2 显示行号

- 更改 *mkdocs.yml*

```
markdown_extensions:
    - codehilite:
        linenums: true
```

### 例3 用冒号代替反引号

- 用法

```
        :::python
        import tensorflow as tf
```

- 效果

        :::python
        import tensorflow as tf

### 例4 指定行高亮

- 用法

```
​``` python hl_lines="3 4"
""" Bubble sort """
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
​```
```

- 效果

``` python hl_lines="3 4"
""" Bubble sort """
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

### 例6 可切换代码块

- 用法

```
​``` bash tab="Bash"
#!/bin/bash
        
echo "Hello world!"
​```
        
​``` c tab="C"
#include <stdio.h>
        
int main(void) {
    printf("Hello world!\n");
}
​```
        
​``` c++ tab="C++"
#include <iostream>
        
int main() {
    std::cout << "Hello world!" << std::endl;
    return 0;
}
​```
        
​``` c# tab="C#"
using System;
    
class Program {
    static void Main(string[] args) {
        Console.WriteLine("Hello world!");
    }
}
​```
```

- 效果
    - 需要装 *pygment* 才有效果
    - 效果像浏览器的页面那样可以切换

## 2. 引用

### 准备

- 编辑 *mkdocs.yml*

```
markdown_extensions:
  - admonition
```

### 操作

- 写法

```
!!! note
    这是一条 note。
```

- 效果

!!! note
    这是一条 note。


## 3. 注脚

### 准备

- 编辑 *mkdocs.yml*

```
markdown_extensions:
  - footnotes
```

### 例1 单行注脚

- 写法

```
跳转到页面底部的脚注1[^1]


[^1}: 点此回去
```

- 效果

跳转到页面底部的脚注1[^1]

### 例2 段落注脚

- 写法

```
跳转到页面底部的脚注2[^2]


[^2]:
    段落需要另起一行写
    有缩进
    缩进必须是四个空格
```

- 效果

跳转到页面底部的脚注2[^2]

## 3. *PyMdom* 推荐的配置

```
markdown_extensions:
    - pymdownx.arithmatex
    - pymdownx.betterem:
        smart_enable: all
    - pymdownx.caret
    - pymdownx.critic
    - pymdownx.details
    - pymdownx.emoji:
        emoji_generator: !!python/name:pymdownx.emoji.to_svg
    - pymdownx.inlinehilite
    - pymdownx.magiclink
    - pymdownx.mark
    - pymdownx.smartsymbols
    - pymdownx.superfences
    - pymdownx.tasklist:
        custom_checkbox: true
    - pymdownx.tilde
```

## 4. 其他的功能与用法

### 4.1 下划线

- 写法

`^^下划线^^`

- 效果

^^下划线^^

### 4.2 *emoji*

- 需要在 *mkdocs.yml* 中添加一句 `emoji_index: !!python/name:pymdownx.emoji.twemoji`
- 不写也行，加上这句，显示的图标更好看

```
markdown_extensions:
    ...
    - pymdownx.emoji:
        emoji_index: !!python/name:pymdownx.emoji.twemoji
        emoji_generator: !!python/name:pymdownx.emoji.to_svg
    ....
```

- 写法

`:tada:`

- 效果

:tada:

### 4.3 *mark*

- 写法

`==mark==`

- 效果

==mark==

### 4.4 单行高亮

- 写法

> \#!js var test = 0;

- 效果

`#!js var test = 0;`

[^1]: 点此回去
[^2]:
    段落需要另起一行写
    有缩进
    缩进必须是四个空格