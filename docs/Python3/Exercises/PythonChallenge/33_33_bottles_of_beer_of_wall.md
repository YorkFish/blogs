# 第 *33* 题 *33 bottles of beer on the wall*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/rock/beer.html" target="_blank">>>> http://www.pythonchallenge.com/pc/rock/beer.html</a>

## 2. 图片

![beer](.\imgs\33_beer1.jpg)

## 3. 提示

- 网页源码注释

    > If you are blinded by the light, 
    > remove its power, with its might. 
    > Then from the ashes, fair and square, 
    > another truth at you will glare.

## 4. 解法

### part1

1. 图片名为 `bear1.jpg`，按照惯例，改地址，得到 `bear2.jpg`

![beer2](.\imgs\beer2.jpg)

2. 再改，改为 `beer2.png`，得到一张灰度图

![beer2](.\imgs\beer2.png)

### part2

- 网页源码提示中的关键字
    - `light, ashes`
    - `fair, square`
- 思路：
    - 对图中各像素按颜色分组，若某颜色的个数是平方数，则记录下来
    - 从最亮的颜色 `255` 开始，依次提取颜色

```python
from PIL import Image

img = Image.open("beer2.png")
ashes = list(img.getdata())
n = len(ashes)
lights = img.getcolors()
lights.reverse()
print(lights)
print(len(lights))

wall = []
for num, _ in lights:
    n -= num
    tmp = n ** 0.5
    if tmp == int(tmp):
        wall.append(tmp)
print(wall)
print(len(wall))

>>>
[(272, 194), (1348, 193), (283, 188), (241, 187), (318, 182), (198, 181), (337, 176), (171, 175), (317, 170), (183, 169), (317, 164), (175, 163), (323, 158), (161, 157), (324, 152), (152, 151), (323, 146), (145, 145), (342, 140), (118, 139), (342, 134), (110, 133), (327, 128), (117, 127), (198, 122), (238, 121), (183, 116), (32, 115), (310, 110), (114, 109), (224, 104), (192, 103), (505, 98), (104, 97), (257, 92), (139, 91), (341, 86), (47, 85), (354, 80), (26, 79), (164, 74), (23, 73), (298, 68), (70, 67), (356, 62), (181, 61), (609, 56), (79, 55), (225, 50), (107, 49), (357, 44), (126, 43), (339, 38), (126, 37), (328, 32), (119, 31), (424, 26), (144, 25), (243, 20), (549, 19), (329, 14), (724, 13), (189, 8), (963, 7), (232, 2), (1532, 1)]
66
[132.0, 130.0, 128.0, 126.0, 124.0, 122.0, 120.0, 118.0, 116.0, 114.0, 112.0, 110.0, 108.0, 107.0, 105.0, 103.0, 100.0, 98.0, 96.0, 94.0, 93.0, 91.0, 88.0, 84.0, 82.0, 79.0, 76.0, 73.0, 69.0, 63.0, 54.0, 42.0, 0.0]
33
```

- 分析结果
    - 194 - 193 = 1, 188 - 187 = 1, 182 - 181 = 1 ...
    - 若 for 语句中不用 if 筛选，会发现 wall 中的平方数也是间隔的

### part3

```python
from PIL import Image

img = Image.open("beer2.png")
ashes = list(img.getdata())
max_value = max(ashes)
for i in range(33):
    data = [ash == max_value for ash in ashes]
    side = int(len(data) ** 0.5)
    res = Image.new('1', (side, side))
    res.putdata(data)
    res.save(f"./beer/33_{i+1:0>2}.png")
    ashes = [ash for ash in ashes if ash < max_value-1]
    max_value = max(ashes, default=-1)
```

- 与第 25 题类似，这一关可以得到 33 张图片

    ![result](.\imgs\33_result.png)

- 将带框的图片依次组合，可得到 `gremlins`

## 5. 答案

- `http://www.pythonchallenge.com/pc/rock/gremlins.html`

## 6. 后记

```txt
Temporary End


Thank you for playing the Python Challenge.
More levels will come soon. You can find if
there are new levels by checking the homepage
or at the Python Challenge News Forum. You can
also subscribe to the news forum by RSS.

If you have ideas for new levels please send me
using the forums.

thesamet
```