# 第 *14* 题 *walk around*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/italy.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/italy.html</a>

## 2. 题图与提示图

- 题图

    ![italy](.\imgs\14_italy.jpg)

- 提示图

    ![wire](.\imgs\14_wire_rect.png)

- ps
    
    - 若直接保存提示图，会得到 `1000X1` 像素的图片，下方程序用到的也是这张

## 3. 提示

- 网页源码注释

    > remember: 100*100 = (100+99+99+98) + (..

## 4. 解法

### part1

1. 将注释中的式子补全

    ```txt
    100 * 100 = (100 + 99 + 99 + 98) +
                ( 98 + 97 + 97 + 96）+
                ... +
                (  4 +  3 +  3 +  2) +
                (  2 +  1 +  1 +  0)
    ```

2. 将那张 `1000X1` 的图片像一条冬眠的 `Python` 一样“盘起来”
3. 方向：按题图中的来，即顺时针、从外部向里面
4. 注释中的数字是每次排版的边长

### part2

#### 方法一

```python
from PIL import Image

img = Image.open("wire.png")
new = Image.new(img.mode, (100, 100))

i = 0
row_begin = col_begin = 0
row_end = col_end = 99
for _ in range(100*2 -1):
    for j in range(col_begin, col_end+1):
        pixel = img.getpixel((i, 0))
        new.putpixel((row_begin, j), pixel)
        i += 1
    row_begin += 1
    
    for j in range(row_begin, row_end+1):
        pixel = img.getpixel((i, 0))
        new.putpixel((j, col_end), pixel)
        i += 1
    col_end -= 1
    
    for j in range(col_end, col_begin-1, -1):
        pixel = img.getpixel((i, 0))
        new.putpixel((row_end, j), pixel)
        i += 1
    row_end -= 1
    
    for j in range(row_end, row_begin-1, -1):
        pixel = img.getpixel((i, 0))
        new.putpixel((j, col_begin), pixel)
        i += 1
    col_begin += 1

new.save("14_result.png")
```

- 生成一张图片

    ![cat](.\imgs\14_result.png)

#### 方法二

```python
from PIL import Image

img = Image.open("wire.png")
delta = [(1, 0), (0, 1), (-1, 0), (0, -1)]  # right, down, left, up
res = Image.new("RGB", [100, 100])  # tuple or list

x, y = -1, 0
cnt = 0
d = 200
while d / 2 > 0:
    for v in delta:
        steps = d // 2
        for s in range(steps):
            x, y = x + v[0], y + v[1]
            res.putpixel((x, y), img.getpixel((cnt, 0)))
            cnt += 1
        d -= 1  # (100,) 99, 99, 98...
res.save("14_result.jpg")
```

- 这次生成的图片是正的

    ![cat](.\imgs\14_result.jpg)

- 关键字：`cat`

### part3

1. 登入网址：`http://www.pythonchallenge.com/pc/return/cat.html`
2. 得到一张图片（此图没有题号，故不是下一关）

    ![cat](.\imgs\14_uzi.jpg)

3. 外加一句提示

    > and its name is **uzi**. you'll hear from him later.
    
4. 关键字：`uzi`，经检验，此为答案

### other

- *part2* 生成的图片上有红点，探索后发现，这些是“温馨提示”
- 如果是直接按行叠加得到的图片

    ```python
    from PIL import Image
    
    img = Image.open("wire.png")
    new = Image.new(img.mode, (100, 100))
    new.putdata(img.getdata())
    new.show()
    ```

- 这些红点会拼成红字：`bit`

    ![wrong](.\imgs\14_wrong_result.png)

- 登入 `http://www.pythonchallenge.com/pc/return/bit.html`，只能得到
    
    > you took the wrong curve.

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/uzi.html`