# 第 *7* 题 *smarty*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/def/oxygen.html" target="_blank">>>> http://www.pythonchallenge.com/pc/def/oxygen.html</a>

## 2. 题图

![oxygen](.\imgs\07_oxygen.png)

## 3. 提示

- 无

## 4. 解法

### part1

1. 图中让人在意的无疑就是中间的那条马赛克似的横线
2. 使用截图工具查看，可发现
    - “马赛克”处每种颜色各自的 `R, G, B` 三值相等
    - 每个色块宽约 *7*，总长约 *609*
    - `h = 50` 这一行经过所有的色块

### part2

1. 使用 `pillow` 提取该线
2. 通过 `R, G, B` 分离，检验 `R == G == B`

    ```python
    from PIL import Image
    
    f = open("07_RGB.txt", 'w')
    img = Image.open("oxygen.png")
    pix = img.load()
    for w in range(3, 609, 7):
        r, g, b, a = pix[w, 50]
        f.write(str((r, g, b, a)) + '\n')
    f.close()
    ```

### part3

1. 将 *RGB* 转 *ASCII*，因为三值相等，故只提取其一即可

    ```python
    from PIL import Image
    
    f = open("07_RGB2ASCII.txt", 'w')
    img = Image.open("oxygen.png")
    pix = img.load()
    for w in range(3, 609, 7):
        r, _, _, _ = pix[w, 50]
        f.write(chr(r))
    f.close()
    ```

2. 查看 `07_RGB2ASCII.txt`
   
    > smart guy, you made it. the next level is [105, 110, 116, 101, 103, 114, 105, 116, 121]

### part4

- 对列表中的数字再做一次 *ASCII* 转换

    ```python
    >>> lst = [105, 110, 116, 101, 103, 114, 105, 116, 121]
    >>> bytes([c for c in lst])
    b'integrity'
    >>> 
    ```

## 5. 答案

- `http://www.pythonchallenge.com/pc/def/integrity.html`