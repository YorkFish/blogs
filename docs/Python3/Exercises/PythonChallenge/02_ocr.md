# 第 *2* 题 *ocr*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/def/ocr.html" target="_blank">>>> http://www.pythonchallenge.com/pc/def/ocr.html</a>

## 2. 题图

![orc](.\imgs\02_ocr.jpg)

## 3. 提示

> recognize the characters. maybe they are in the book,
> but MAYBE they are in the page source.

## 4. 解法

1. 根据提示，查看网页源码，有一短一长两段注释

    ```txt
    find rare characters in the mess below:
    
    %%$@_$^__#)^)&!_+]!*@&^}@[@%]()%+$&...  # 略去千余行
    ```

2. 既然是“寻找稀有字符”，那么这一题是“统计词频”了
3. 方便起见，我将上述乱码另存为 `ocr.txt`

### 4.1 方法一

```python
with open("ocr.txt") as f:
    d = {}
    for e in f.read():
        d[e] = d.get(e, 0) + 1
    lst = [e for e in d.keys()]
    lst.sort(key=lambda x: d[x])
    print(''.join(lst))

>>>
equality
^*&${+!%}[_#](@)
```

### 4.2 方法二

- 由方法一的结果可知需要获取的是只出现一次的字符

```python
from collections import Counter

with open("ocr.txt") as f:
    c = Counter(f.read())
    res = [e for e in c if c[e] == 1]
    print(''.join(res))

>>>
equality
```

## 5. 答案

- `http://www.pythonchallenge.com/pc/def/equality.html`