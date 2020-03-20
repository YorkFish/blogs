# 第 *4* 题 *follow the chain*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/def/linkedlist.php" target="_blank">>>> http://www.pythonchallenge.com/pc/def/linkedlist.php</a>

## 2. 题图

![chainsaw](.\imgs\04_chainsaw.jpg)

## 3. 提示

- 网页源码注释

    > urllib may help. DON'T TRY ALL NOTHINGS, since it will never
    > end. 400 times is more than enough.

## 4. 解法

1. 图片可以点击
    - 点击后，页面跳转至 `http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345`
    - 新页面内容：`and the next nothing is 44827`
2. 用页面的 `next nothing` 值替换网址中 `nothing` 的值，会跳转至新页面并得到新的 `next nothing` 值
3. 提示中推荐使用 `urllib`，并告知这样的网页有 *400* 个左右，并且循环
4. 对于 *Python3*，`request` 也是一个不错的选择

    ```python
    from re import findall
    from requests import get
    
    url = "http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing="
    num = 44827
    res = get(url + str(num))
    try:
        while True:
            num = findall(r"\d{3,}", res.text)[0]
            print(num)
            res = get(url + num)
    except:
        print(res.text)
    
    >>>
    ...  # 此处略去百余项
    16044
    Yes. Divide by two and keep going.
    ```

5. 取 *16044* 的一半为值，继续（我换了个方法）

    ```python
    from requests import get
    
    num = 16044 // 2
    while True:
        res = get(f"http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing={num}")
        num = res.text.split()[-1]
        if num.isdigit():
            print(num)
        else:
            print(res.text)
            break
    
    >>>
    ...  # 此处略去百余项
    66831
    peak.html
    ```

## 5. 答案

- `http://www.pythonchallenge.com/pc/def/peak.html`