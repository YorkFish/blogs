# 第 *11* 题 *odd even*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/5808.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/5808.html</a>

## 2. 题图

![cave](.\imgs\11_cave.jpg)

## 3. 提示

- 无

## 4. 解法

### part1

1. 此图像是从玻璃窗上看到的，有“倒影”
2. 标题暗示把图像按“奇偶”分成两张
3. 至于是什么的奇偶，大胆猜测：像素的序号（从 *0* 开始）

### part2

1. 从题图中取一块并放大

    ```python
    from PIL import Image
    
    img = Image.open("cave.jpg")
    small = img.crop((0, 0, 10, 5))
    big = small.resize((500, 250))
    big.save("11_crop_resize.png")
    ```

2. 得到如下图片

    ![crop_resize](.\imgs\11_crop_resize.png)

3. 得到如下规律（单位：像素，从 *0* 开始计算）
    - 偶数行
        - 偶数列属于图一
        - 奇数列属于图二
    - 奇数行
        - 偶数列属于图二
        - 奇数列属于图一

### part3

#### 方法一

```python
from PIL import Image

img = Image.open("cave.jpg")
w, h = img.size
one = Image.new(img.mode, (w//2, h))
two = one.copy()

for x in range(w):
    for y in range(h):
        pixel = img.getpixel((x, y))
        if x % 2 == 0:
            if y % 2 == 0:
                one.putpixel((x//2, y), pixel)
            else:
                two.putpixel((x//2, y), pixel)
        else:
            if y % 2 == 0:
                two.putpixel((x//2, y), pixel)
            else:
                one.putpixel((x//2, y), pixel)
one.save("11_even.png")
two.save("11_odd.png")
```

- 图 *even*

    ![even](.\imgs\11_even.png)

- 图 *odd*

    ![odd](.\imgs\11_odd.png)

#### 方法二

```
from PIL import Image

img = Image.open("cave.jpg")
w, h = img.size
res = Image.new(img.mode, (w//2, h))
for x in range(w):
    for y in range(h):
        if not x % 2 ^ y % 2:
            res.putpixel((x//2, y), img.getpixel((x, y)))
res.show()
```

- 得到的图片与上方的 *even* 一致，而图中的 `evil` 正是此题的解

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/evil.html`