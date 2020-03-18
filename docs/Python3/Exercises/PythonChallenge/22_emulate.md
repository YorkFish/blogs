# 第 *22* 题 *emulate*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/hex/copper.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/copper.html</a>

## 2. 图片

![level22](.\imgs\22_level22.jpg)

## 3. 提示

- 网页源码注释

    > or maybe white.gif would be more bright

## 4. 解法

### part1

1. 根据注释提示，来到 `http://www.pythonchallenge.com/pc/hex/white.gif`，并得到图片

    ![white](.\imgs\22_white.gif)

2. 图片是 `gif` 格式，尺寸：`200x200`

3. 图片一片漆黑，却有 39k

4. 使用“十六进制编辑器”打开图片，为文件头 `47 49 46 38 39 61 c8 00 c8 00 ...`

    - 有过第 12 题的经验，可知前 6 组个字节对应 `GIF89a`
    - `c8` 的十进制是 `200`，故后 4 个字节对应图片尺寸
    - 从第 14 个字节开始，3 个数据一组，表示调色板信息
    - 再往下走，还能看到 `NETSCAPE2.0` 和 `Created with The GIMP `
    - 再往下走，还能看到 `c800c800`，且不止一次，这说明此图是由好几帧图片合成的动图
### part2

1. 查看颜色分布

    ```python
    >>> from PIL import Image
    >>> gif = Image.open("white.gif")
    >>> gif.size
    (200, 200)
    >>> data = getdata()
    >>> len(data)
    40000  # 200x200
    >>> gif.getcolors()
    [(39999, 0), (1, 8)]
    >>> 
    ```

2. 仅一点为 8 号色，这是关键

    ```python
    >>> f = open("white.gif", "rb")
    >>> data = f.read()
    >>> data.index(8)
    37
    >>> new = data[:37] + b"\xff\xff\xff" + data[40:]  # 将八号色对应的点改为白色
    >>> g = open("22_new_White.gif", "wb")
    >>> g.write(new)
    38979
    >>> g.close()
    >>> 
    ```

3. 得到一张动图

    ![new_White](.\imgs\22_new_white.gif)

4. 作者之意大概就是：这个小白点，就像手柄在屏幕上对应的图标
5. 小白点像是在写字，接下来的任务就是把它的路径记录下来

### part3

1. 获取图像的帧数

    ```python
    from PIL import Image
    
    gif = Image.open("white.gif")
    frame = 0
    while True:
      try:
        gif.seek(frame)
        frame += 1
      except:
        break
    
    print(frame)
    gif.close()
    
    >>>
    133
    ```

2. 该图有 133 帧

### part4

1. 记录小白点路径

    ```python
    from PIL import Image
    
    gif = Image.open("white.gif")
    frame = 0
    while True:
      try:
        gif.seek(frame)
        frame += 1
        x, y, _, _ = gif.getbbox()
        print(f"({x:>3}, {y:>3})")
      except:
        break
    gif.close()
    
    >>>
    (100, 100)
    (100, 102)
    (100, 102)
    (100, 102)
    (100, 102)
    (100, 102)
    (100, 102)
    (100, 102)
    (100, 102)
    (102, 102)
    (102, 100)
    (102, 100)
    (102, 100)
    (102, 100)
    (102, 100)
    (102, 100)
    (102, 100)
    (102,  98)
    ...
    ```

4. 看上去很像笔画，一竖、一横的，而且是相对图片中心在动

5. 记录相对中心的距离

    ```python
    from PIL import Image
    
    
    def get_movements(f):
        ox = oy = 100
        lst = []
        for frame in range(133):
            f.seek(frame)
            x, y, _, _ = f.getbbox()
            lst.append((ox-x, oy-y))
        return lst
    
    
    if __name__ == "__main__":
        gif = Image.open("white.gif")
        res = get_movements(gif)
        gif.close()
    
        print(list(res))
        print('=' * 30)
        print(set(res))
    
    
    >>>
    [(0, 0), (0, -2), (0, -2), (0, -2), (0, -2), (0, -2), (0, -2), (0, -2), (0, -2), (-2, -2), (-2, 0), (-2, 0), (-2, 0), (-2, 0), (-2, 0), (-2, 0), (-2, 0), (-2, 2), (0, 2), (0, 2), (0, 2), ...
    ==============================
    {(0, 0), (-2, 0), (2, 2), (-2, 2), (2, -2), (2, 0), (-2, -2), (0, -2), (0, 2)}
    ```

6. 除去 `(0, 0)`，共有 8 种方向，这正对应手柄的八个方向

### part5

```python
from PIL import Image


def get_movements(f):
    ox = oy = 100
    lst = []
    for frame in range(133):
        f.seek(frame)
        x, y, _, _ = f.getbbox()
        lst.append((ox-x, oy-y))
    return lst


def get_script1(lst):
    white = 255
    side = 300
    x = y = side // 2
    img = Image.new('P', (side, side), 0)
    for dx, dy in lst:
        x += dx
        y += dy
        img.putpixel((x, y), white)
    img.show()


def get_script2(lst):
    cnt = 0
    for t in lst:
        if t == (0, 0):
            cnt += 1
    print(cnt)


def get_script3(lst):
    white = 255
    x = y = 50
    img = Image.new('P', (500, 100), 0)
    cnt = 0
    for dx, dy in lst:
        if dx == dy == 0:
            x = 50 + cnt * 100
            y = 50
            cnt += 1
        else:
            x += dx  # 这样做，每个字母都需要顺时针转 180°
            y += dy
        img.putpixel((x, y), white)
    img.show()


def get_script4(lst):
    white = 255
    x = y = 50
    img = Image.new('P', (500, 100), 0)
    cnt = 0
    for dx, dy in lst:
        if dx == dy == 0:
            x = 50 + cnt * 100
            y = 50
            cnt += 1
        else:
            x -= dx
            y -= dy
        img.putpixel((x, y), white)
    img.save("22_result.gif")


if __name__ == "__main__":
    gif = Image.open("white.gif")
    res = get_movements(gif)
    gif.close()
    # get_script1(res)  # 字母重叠在一起
    # get_script2(res)  # 5 -> 5 letters
    # get_script3(res)
    get_script4(res)
```

![result](.\imgs\22_result.gif)

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/bonus.html`