# LaTeX

## 1. 用法

- `$$ + 编辑的内容 + $$`

## 2. 说明

### 2.1 几个名词解释

| 名称 | 释义 |
| :---: | :--- |
| TeX | 学术排版 |
| LaTe | 相当于 TeX 的简化版本；对公式编辑精细至像素级别 |
| MathJax | 相当于 LaTeX 的简化版本，用于显示数学表达式式 |
| Markdown | 不支持 TaTeX 所有的语法，对数学公式的支持比较好 |

### 2.2 使用 *MkDocs* 的情况

- 方法更新了，5.x 的使用方法是在 `mkdocs.yml` 中添加如下 code

        extra_javascript:
            - https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-MML-AM_CHTML

### 2.3 注意事项

- 注意：`LaTex` 是区分大小写的
- 这里可以使用单行公式，这是一般的 *Markdown* 不具备的

## 3. 示例与效果

- 示例（借用一下勒让德的“素数定理”）

```
$$
\pi(x) = \int_0^x \frac{dt}{lnt} + C
$$
```

- 效果

    $$
    \pi(x) = \int_0^x \frac{dt}{lnt} + C
    $$

### 补充例子

- 单行示例
    - 素数定理：`$\pi(x) = \int_0^x \frac{dt}{lnt} + C$`
    - 单个字符 `$C$` 也行

- 效果
    - 素数定理：$\pi(x) = \int_0^x \frac{dt}{lnt} + C$
    - 单个字符 $C$ 也行
