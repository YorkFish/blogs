# 第 *16* 题 *let me get this straight*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/return/mozart.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/mozart.html</a>

## 2. 图片

![mozart](.\imgs\16_mozart.gif)

## 3. 提示

- 无

## 4. 解法

### part1

1. 图中有许多紫色线段，放大后看是这样的

    ![enlarge](.\imgs\16_local_enlarge.png)

2. 第 *14* 题有 `1000X1` 的图片，此图为 `640X480`

    - 可将此图看成是 480 个 `640X1` 的图片层叠而成
    
3. 检验每个 `640X1` 区域中紫色线段的数量（使用截图工具测量，紫色线段约 5 个像素）

    ```python
    from PIL import Image
    
    
    def check_lines(filename):
        img = Image.open(filename)
        w, h = img.size
        res = []
        for line_num in range(h):
            line = []
            cnt = 1
            pix = img.getpixel((0, line_num))
            for i in range(1, w):
                tmp = img.getpixel((i, line_num))
                if tmp == pix:
                    cnt += 1
                else:
                    pix = tmp
                    cnt = 1
                if cnt == 5:
                    line.append(tmp)
                    cnt = 1
            res.append(line)
        return res
    
    
    if __name__ == "__main__":
        filename = "16_mozart.gif"
        print(check_lines(filename))
    ```

4. 结论

    - 每行均有连续 5 个像素一致的值
    - 连续 5 个 `195` 在每行都出现了一次

5. 关于 `195`
    - 题图为 `.gif` 格式，此格式除了有 `R, G, B`，还有“调色板”信息
    - 0-255 对应 256 种颜色，195 的 `R, G, B` 对应 `(255, 0, 255)`

### part2

1. 可以对 part1 中的结论进行检验

    ```python
    >>> from PIL import Image, ImageChops
    >>> image = Image.open("mozart.gif")
    >>> h = image.histogram()  # [count(0), count(1), ...]
    >>> for num in h:
    ...     if num and num % image.height == 0:
    ...         print(h.index(num), num)
    ...
    195 2400
    >>> 
    ```
2. 640 x 4 = 2400, ok

### part3

- 把每一“条” `640X1` 以紫色线段为开头，多余的部分移到该行末尾

```python
from PIL import Image, ImageChops

image = Image.open("mozart.gif")

for y in range(image.size[1]):
    box = 0, y, image.size[0], y + 1
    row = image.crop(box)
    bytes = row.tobytes()
    i = bytes.index(195)
    row = ImageChops.offset(row, -i)
    image.paste(row, box)

image.save("16_result.gif")
```

![result](.\imgs\16_result.gif)

- 答案就是 `romance`

## 5. 答案

- `www.pythonchallenge.com/pc/return/romance.html`