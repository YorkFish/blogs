# 第 *12* 题 *dealing evil*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/evil.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/evil.html</a>

## 2. 题图

![evil1](.\imgs\12_evil1.jpg)

## 3. 提示

- 无

## 4. 解法

### part1

1. 将题图另存为时发现此图名为 `evil1.jpg`
2. 图片地址：`http://www.pythonchallenge.com/pc/return/evil1.jpg`
3. 将 `evil1` 改为 `evil2`，得到下图

    ![evil2](.\imgs\12_evil2.jpg)

4. 按图中提示，将地址的后缀改为 `.gfx`，可以下载到一个 `evil2.gfx` 的文件
5. 搜索得知，`PS` 支持 `.gfx` 格式，我没有 `PS`，从结果看，这个文件是打不开的

### part2

1. 试试 `evil3`，果然还有图片

    ![evil3](.\imgs\12_evil3.jpg)

2. `evil4` 有些怪，没有图像（实际上它是文本文件），但可以获取信息（下一题有用）

    ![evil4](.\imgs\12_evil4.png)

3. `evil5` 是 `404`，所以到此为止了

### part3

1. 题图中，主角将牌分成了五堆，这是暗示我们将 `evil2.gfx` 分成五份
2. 检查一下数据是否是 *5* 的倍数

    ```python
    img = open("12_evil2.gfx", "rb")
    data = img.read()
    img.close()
    print(len(data))
    
    >>>
    67575
    ```

3. 确定这五张图片的格式

    ```python
    img = open("12_evil2.gfx", "rb")
    data = img.read(80)
    img.close()
    array = [n for n in range(30, 40)] + [n for n in range(65, 91)] + [n for n in range(97, 123)]
    for i in range(5):
        print(''.join([chr(e) for e in data[i::5] if e in array]))
    
    >>>
    JFIF
    PNGIHDR
    GIFa
    PNGIHDR
    JFIF
    ```

4. 关于格式
    - `JFIF -> jpg`
    - `PNGIHDR -> png`
    - `GIFa -> gif`

### part4

```python
f = open("12_evil2.gfx", "rb")
content = f.read()
f.close()
names = ["12_01.jpg", "12_02.png", "12_03.gif", "12_04.png", "12_05.jpg"]
for i in range(5):
    with open(names[i], "wb") as f:
        f.write(content[i::5])
```

- 图一

    ![dis](.\imgs\12_01.jpg)

- 图二

    ![pro](.\imgs\12_02.png)

- 图三

    ![port](.\imgs\12_03.gif)

- 图四

    ![ional](.\imgs\12_04.png)

- 图五

    ![ity](.\imgs\12_05.jpg)

### part5

- 第 *4* 张图是破损的，个人认为有以下三种解释
    1. 对应网页中的无法显示的 `evil4`
    2. 五组等长的数据合成不同格式的图片后，分辨率各异，还出现了破损的图片，结合题图，这可能暗示“赌桌”上存在 `evil`
    3. 也许作者是想让我们通过四张正常的图片推测剩下的这张
- 第 *4* 张图片虽然破损，但仍能辨认出，而将前四张图中的字母连起来，可得到：`disproportional`

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/disproportional.html`