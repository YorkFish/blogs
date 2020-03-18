# 第 *27* 题 *between the tables*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/hex/speedboat.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/speedboat.html</a>

## 2. 图片

![zigzag](.\imgs\27_zigzag.jpg)

## 3. 提示

- 网页源码注释

   ```txt
   <img src="zigzag.jpg"> <!-- did you say gif? -->
   
   oh, and this is NOT a repeat of 14
   ```

## 4. 解法

### part1

1. 图片可以点进去，新的页面的地址为：`http://www.pythonchallenge.com/pc/ring/bell.html`
2. 需要输入用户名与密码，看来账号、密码又一次更新了
3. 按网页源码注释的第一条提示：将图片的地址后缀改为 `gif`
4. 获得一张灰度图

    ![zigzag](.\imgs\27_zigzag.gif)

### part2

1. 查看灰度图的**调色板值**与**RGB 值**

    ```python
    >>> from PIL import Image
    >>> img = Image.open("zigzag.gif")
    >>> data = list(img.getdata())
    >>> data[:12]
    [215, 208, 203, 12, 254, 60, 139, 72, 66, 189, 127, 176]
    >>> 
    >>> 
    >>> colors = img.getpalette()
    >>> colors[:9]
    [37, 37, 37, 229, 229, 229, 162, 162, 162]
    >>> colors = colors[::3]
    >>> 
    >>> 
    >>> colors[215]
    208
    >>> colors[208]
    203
    >>> colors[203]
    12
    >>> 
    ```

2. `data` 中的在 `colors` 数据像
    - 一个链表，`215 -> 208 -> 203 -> ...`
    - 第 24 题中，用 BFS 构建迷宫路线的字典
    - 题图中左下角的 `zigzag`

3. 查看是否尾对头

    ```python
    >>> data[-2:]
    [250, 100]
    >>> colors[250]
    100
    >>> colors[100]
    93  # not 215
    >>> 
    ```

4. 因为尾部对不上，所以有必要查看中间有没有对不上

    ```python
    from PIL import Image
    
    img = Image.open("zigzag.gif")
    colors = img.getpalette()[::3]
    data1 = list(img.getdata())
    data2 = [colors[i] for i in data1]
    data1.append(data1.pop(0))
    
    lst = [1 for i,j in zip(data1, data2) if i!=j]
    print(sum(lst))
    
    >>>
    9465
    ```

5. 探索一番，发现：将 `data1` 与 `data2` 不匹配之处的数据转换成 `ascii` 后有熟悉的身影

    ```python
    from PIL import Image
    
    img = Image.open("zigzag.gif")
    colors = img.getpalette()[::3]
    data1 = list(img.getdata())
    data2 = [colors[i] for i in data1]
    data1.append(data1.pop(0))
    
    lst = [chr(i) for i,j in zip(data1, data2) if i!=j]
    print(lst[:10])
    
    >>>
    ['B', 'Z', 'h', '9', '1', 'A', 'Y', '&', 'S', 'Y']
    ```

### part3

1. 使用 `bz2` 解码

    ```python
    from bz2 import decompress
    from PIL import Image
    
    img = Image.open("zigzag.gif")
    colors = img.getpalette()[::3]
    data1 = list(img.getdata())
    data2 = [colors[i] for i in data1]
    data1.append(data1.pop(0))
    
    s = [i for i,j in zip(data1, data2) if i!=j]
    text = decompress(bytes(s))
    print(text)
    
    >>>
    b'../ring/bell.html del assert repeat raise or class is exec return except print return switch from exec repeat else not while assert or class class break except assert yield finally ../ring/bell.html assert ../ring/bell.html ...
    ```

2. 分析解码后的内容
    - 包含许多 Python 关键字（准确地说，是 Python2 的关键字）
    - 有许多内容是重复的

3. 先去关键字，再去重

    ```python
    from bz2 import decompress
    from keyword import iskeyword
    from PIL import Image
    
    img = Image.open("zigzag.gif")
    colors = img.getpalette()[::3]
    data1 = list(img.getdata())
    data2 = [colors[i] for i in data1]
    data1.append(data1.pop(0))
    
    s = [i for i,j in zip(data1, data2) if i!=j]
    text = decompress(bytes(s))
    print(set([w for w in text.split() if not iskeyword(w.decode())]))
    
    >>>
    {b'switch', b'exec', b'../ring/bell.html', b'repeat', b'print'}
    ```

4. 说明：在 Python3 中，`exec` 与 `print` 已经不是关键字了，所以作者的原意是
    - `../ring/bell.html`
    - `repeat`
    - `switch`

5. 经检验，账号是 `repeat`，密码是 `switch`

## 5. 答案

- `http://www.pythonchallenge.com/pc/ring/bell.html`
    - 账号：`repeat`
    - 密码：`switch`