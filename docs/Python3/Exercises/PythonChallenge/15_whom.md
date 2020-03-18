# 第 *15* 题 *whom*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/return/uzi.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/uzi.html</a>

## 2. 图片

![screen](.\imgs\15_screen15.jpg)

## 3. 提示

- 网页源码注释

    > he ain't the youngest, he is the second
    >
    > todo: buy flowers for tomorrow

## 4. 解法

### part1

1. 年份范围：`1xx6`
2. 该年的 1 月 26 日是周一
3. 题图右下角的二月有 29 天，所以这一年是闰年

```python
from datetime import datetime

for y in range(1006, 1997, 10):
    date = datetime(y, 1, 26)
    if date.weekday() == 0:  # 周六对应 0
        if date.year % 4 == 0:  # 1xx6 年只需判断是否为 4 的倍数
            print(date.year)

>>>
1176
1356
1576
1756
1976
```

### part2

1. 因为是第二年轻，所以是 1756
2. 因为第二天要买花，所以 1756-1-27 可能是纪念日，搜索得知是奥地利作曲家**莫扎特** `mozart`

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/mozart.html`