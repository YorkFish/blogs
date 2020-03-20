# 第 *10* 题 *what are you looking at?*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/bull.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/bull.html</a>

## 2. 题图

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
4. 方法有许多，我来个抛砖引玉

    ```python
    num = "1"
    for i in range(30):
        s = ''
        cnt = 1
        t = num[0]
        for c in num[1:]:
            if t == c:
                cnt += 1
            else:
                s += str(cnt) + t
                cnt = 1
                t = c
        s += str(cnt) + t
        num = s
    print(len(num))
    
    >>>
    5808
    ```

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/5808.html`