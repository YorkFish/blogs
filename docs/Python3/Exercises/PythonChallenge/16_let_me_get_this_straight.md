# 第 *16* 题 *let me get this straight*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/mozart.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/mozart.html</a>

## 2. 题图

![mozart](.\imgs\16_mozart.gif)

## 3. 提示

- 无

## 4. 解法

### part1

1. 图中有许多紫色线段，放大后看是这样的

    ![enlarge](.\imgs\16_local_enlarge.png)

2. 第 *14* 题有 `1000X1` 的图片，此图为 `640X480`
   
    - 可将此图看成是 *480* 个 `640X1` 的图片层叠而成
3. 检验每个 `640X1` 区域中紫色线段的数量（使用截图工具测量，紫色线段约 *5* 个像素）

    ```python
    from PIL import Image
    from pprint import pprint
    
    
    def check_lines(filename):
        img = Image.open(filename)
        w, h = img.size
        res = []
        for line_num in range(h):
            line = []
            pix = img.getpixel((0, line_num))
            cnt = 1
            for i in range(1, w):
                tmp = img.getpixel((i, line_num))
                if tmp == pix:
                    cnt += 1
                else:
                    pix = tmp
                    cnt = 1
                if cnt == 5:
                    line.append(tmp)
            res.append(line)
        return res
    
    
    if __name__ == "__main__":
        filename = "mozart.gif"
        pprint(check_lines(filename))
    ```

4. 结论
    - 每行均有连续 *5* 个像素一致的值
    - 有些行这样的值不值一个
    - 唯独 `195` 在每行都出现了一次
5. 关于 `195`
    - 题图为 `.gif` 格式，此格式除了有 `R, G, B`，还有“调色板”信息
    - *0-255* 对应 *256* 种颜色，*195* 的 `R, G, B` 对应 `(255, 0, 255)`

### part2

1. 可以对 *part1* 中的结论进行检验

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
2. 640 x 5 = 2400, ok

### part3

1. 把每一“条” `640X1` 以紫色线段为开头，多余的部分移到该行末尾

    ```python
    from PIL import Image, ImageChops
    
    img = Image.open("mozart.gif")
    
    for y in range(img.size[1]):
        box = 0, y, img.size[0], y + 1
        row = img.crop(box)
        row_bytes = row.tobytes()
        i = row_bytes.index(195)
        row = ImageChops.offset(row, -i)  # like 'crol' in c
        img.paste(row, box)
    
    img.save("16_result.gif")
    ```

2. 得到图片

    ![result](.\imgs\16_result.gif)

3. 得到答案：`romance`

## 5. 答案

- `www.pythonchallenge.com/pc/return/romance.html`