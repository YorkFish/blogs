# 第 *17* 题 *eat?*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/romance.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/romance.html</a>

## 2. 题图

![cookies](.\imgs\17_cookies.jpg)

## 3. 提示

- 此题图的左下角为第 *4* 题的题图

## 4. 解法

### part1

1. 回到第 *4* 题：`http://www.pythonchallenge.com/pc/def/linkedlist.php`
2. 饼干的英文：*cookie*
3. 本题的题图名为 `cookies`
3. 根据作者的提示，查看网页的 `cookie`

    ![cookie](.\imgs\17_cookie.png)

### part2

1. 点击第 *4* 题的题图
2. 将 `nothing` 改为 `busynothing`
    
    - `http://www.pythonchallenge.com/pc/def/linkedlist.php?busynothing=12345`
3. 网页跳转，并得到如下信息

    > If you came here from level 4 - go back!
    > You should follow the obvious chain...
    >
    > and the next busynothing is 44827

4. 更改 `busynothing` 的值，查看新网页的 `cookie`，其值为 `B`
5. 看来是要收集 `cookies`

### part3

```python
from requests import get

url = "http://www.pythonchallenge.com/pc/def/linkedlist.php?busynothing="
num = "12345"
lst = []
while num.isdecimal():
    res = get(url + num)
    lst.append(res.cookies.get("info"))
    num = res.text.split()[-1]
    print(num)
print(res.text)

tmp = ''.join(lst)
print(tmp)
with open("17_cookies.txt", 'w') as f:
    f.write(tmp)

>>>
...
83051
it.
that's it.
BZh91AY%26SY%94%3A%E2I%00%00%21%19%80P%81%11%00%AFg%9E%A0+%00hE%3DM%B5%23%D0%D4%D1%E2%8D%06%A9%FA%26S%D4%D3%21%A1%EAi7h%9B%9A%2B%BF%60%22%C5WX%E1%ADL%80%E8V%3C%C6%A8%DBH%2632%18%A8x%01%08%21%8DS%0B%C8%AF%96KO%CA2%B0%F1%BD%1Du%A0%86%05%92s%B0%92%C4Bc%F1w%24S%85%09%09C%AE%24%90
```

- 以 `BZh91` 开头，回想起第 *8* 题

### part4

1. 仔细看上面的 `BZh91...`，会发现有个 `+`，把它替换成空格再解码

    ```python
    from bz2 import decompress
    from urllib.parse import unquote_to_bytes
    
    with open("17_cookies.txt", 'r') as f:
        text = f.readline()
        res = text.replace('+', ' ')
        ans = unquote_to_bytes(res)
        print(decompress(ans))
    
    >>>
    b'is it the 26th already? call his father and inform him that "the flowers are on their way". he\'ll understand.'
    ```

2. *26* 号与 *flower* 说的应该是第 *15* 题
3. *call* 说的应该是第 *13* 题
4. 综合起来，是要用第 *13* 题的 `phone` 跟 `Mozart` 父亲通话
5. 通话内容：`the flowers are on their way`

### part5

1. 搜索得知，`Mozart` 父亲名为：`Leopold`

    ```python
    from xmlrpc.client import ServerProxy
    
    contact = ServerProxy("http://www.pythonchallenge.com/pc/phonebook.php")
    print(contact.phone("Leopold"))
    
    >>>
    555-VIOLIN
    ```

2. “小提琴手” 正是 `Leopold` 的一个身份
3. 打开网页 `http://www.pythonchallenge.com/pc/return/violin.html`，得到

    > no! i mean yes! but ../stuff/violin.php.

5. 得到下一步的网页地址：`http://www.pythonchallenge.com/pc/stuff/violin.php`

    ![leopold](.\imgs\17_leopold.jpg)

6. 此为 `Leopold` 的肖像
    - 图片没有题号，故此题还末结束
    - 图片不是居中，而是在正上方，那么网页下半部分可能隐藏着话

### part6

1. 使用 `the flowers are on their way`

    ```python
    from requests import get
    
    url = "http://www.pythonchallenge.com/pc/stuff/violin.php"
    cookie = {"info": "the flowers are on their way"}
    res = get(url, cookies=cookie)
    print(res.text)
    ```

2. 得到如下信息

    ```html
    <html>
    <head>
      <title>it's me. what do you want?</title>
      <link rel="stylesheet" type="text/css" href="../style.css">
    </head>
    <body>
            <br><br>
            <center><font color="gold">
            <img src="leopold.jpg" border="0"/>
    <br><br>
    oh well, don't you dare to forget the balloons.</font>
    </body>
    </html>
    ```

3. 关键字：`balloons`

### other

- 若使用插件修改 `cookie`，可在 `Leopold` 的肖像下方看到 `oh well, don't you dare to forget the balloons.`

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/balloons.html`