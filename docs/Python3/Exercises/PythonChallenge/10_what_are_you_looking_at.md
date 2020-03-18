# 第 *10* 题 *what are you looking at?*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/return/bull.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/bull.html</a>

## 2. 图片

![bull](.\imgs\10_bull.jpg)

## 3. 提示

> len(a[30]) = ?

## 4. 解法

1. 点击左边的牛，页面跳转，得到一句：`a = [1, 11, 21, 1211, 111221, `
2. 看来是要找规律，得到 `a[30]` 的长度
3. 规律
    - `a[0]` 为初始值，`a[n]` 是对 `a[n-1]` 的解释
    - `a[1]` 的 `11` 表示 `a[0]` 有 1 个 `1`
    - `a[2]` 的 `21` 表示 `a[1]` 有 2 个 `1`
    - `a[3]` 的 `1211` 表示 `a[2]` 有 1 个 `2`，1 个 `1`
    - `a[4]` 的 `111221` 表示 `a[3]` 有 1 个 `1`，1 个 `2`，2 个 `1`

```python
a = ["1", "11", "21", "1211", "111221"]
cnt = 4
while cnt < 30:
    num = a[cnt]
    n = len(num)
    c, e = 1, 0
    s = ''
    for i in range(1, n):
        if num[e] == num[i]:
            c += 1
        else:
            s += str(c) + num[e]
            c, e = 1, i
    s += str(c) + num[e]
    a.append(s)
    cnt += 1
print(len(a[30]))

>>>
5808
```

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/5808.html`