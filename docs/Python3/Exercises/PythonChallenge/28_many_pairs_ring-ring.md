# 第 *28* 题 *many pairs ring-ring*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/ring/bell.html" target="_blank">>>> http://www.pythonchallenge.com/pc/ring/bell.html</a>

## 2. 图片

![ring](.\imgs\28_bell.png)

## 3. 提示

- 网页内

    > RING-RING-RING
    >
    > say it out loud

## 4. 解法

### part1

1. 按第一条提示，`Ring-Ring-Ring` 地多读几遍，像第 5 题的 `pickle` 那样，可以读出 `green`
2. 修改网址，去到：`http://www.pythonchallenge.com/pc/ring/green.html`

3. 得到 `yes! green!`

### part2

1. 查看图片是  `R, G, B, A` 还是 `R, G, B` 的，即检验是否存在 α 通道

    ```python
    >>> from PIL import Image
    >>> img = Image.open("bell.png")
    >>> img.getbands()
    ('R', 'G', 'B')
    >>> 
    ```

2. 使用 `Image.split()` 分离颜色，虽然只需要 `green`，但另两种颜色也不妨看一下

    ```python
    >>> red, green, blue = img.split()
    >>> red.show()
    >>> green.show()
    >>> blue.show()
    >>> green.save("green.png")
    >>> 
    ```

3. 探索 `green.png` 的像素值

    ```python
    >>> data = list(green.getdata())
    >>> data[:10]
    [55, 97, 73, 115, 120, 78, 60, 102, 76, 118]
    >>> [data[i]-data[i+1] for i in range(0,10,2)]
    [-42, -42, 42, -42, -42]
    >>> 
    ```

4. 题外话：《银河系漫游指南》里，“生命、宇宙以及任何事情的终极答案”为 42

5. 上一题的 `zigzag` 看似符合规律，但其中有 `9465` 个例外，这一题也是

    ```python
    >>> t = [abs(i-j) for i,j in zip(data[1::2],data[::2]) if abs(i-j) != 42]
    >>> t
    [119, 104, 111, 100, 117, 110, 110, 105, 116, 40, 41, 46, 115, 112, 108, 105, 116, 40, 41, 91, 48, 93, 32, 63]
    >>> len(t)
    24
    >>> 
    ```

6. 转 `ASCII`，然后打印一下

    ```python
    >>> bytes(t)
    b'whodunnit().split()[0] ?'
    >>> 
    ```

### part3

1. 必应词典中 `whodunit` 的含义
    - 〈美俚〉侦探小说[戏剧,影片等]
    - 网络推理小说；侦探故事；谁是凶手
2. 按第二条提示 `say it out loud`，`whodunit` 读起来像是 `who done it`
3. 这里是说谁创造了 `Python`，当然是 `Guido van Rossum`
4. 此外，`Guido` 读起来像是 `gui do`：`gui` 叔做了这一切

    ```python
    >>> "Guido van Rossum".split()[0]
    'Guido'
    >>> 
    ```

5. 大写不行，转成小写即是解

## 5. 答案

- `http://www.pythonchallenge.com/pc/ring/guido.html`