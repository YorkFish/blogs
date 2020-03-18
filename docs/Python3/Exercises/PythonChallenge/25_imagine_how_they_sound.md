# 第 *25* 题 *imagine how they sound*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/hex/lake.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/lake.html</a>

## 2. 图片

![lake](.\imgs\25_lake1.jpg)

## 3. 提示

- 网页源码注释

    > can you see the waves?

## 4. 解法

### part1

1. 这一题的图片名为 `lake1.jpg`，按之前的规律（如第 12 题），可能有 `lake2, lake3, ...`
2. 按标题的提示，发现 `wave sounds like wav` （如第19 题，有用到 `wav` 模块）
3. 先将网址的 `lake.html` 改为 `lake1.wav` 试试
4. 网页源码注释提示 `waves`，这说明可能有许多 `.wav`，我试了 `lake2.wav` 果然有

### part2

1. 这是第 25 关，而且图中的拼图块也有 25 块，说不定有 25 个 `.wav` 文件

    ```python
    from requests import get
    
    
    def download_one(filename):
        url = "http://www.pythonchallenge.com/pc/hex/" + filename
        res = get(url, auth=("butter", "fly"))
        if res.ok:
            f = open(filename, "wb")
            f.write(res.content)
            f.close()
            return True
        else:
            return False
    
    
    def download_all():
        n = 1
        while True:
            filename = f"lake{n}.wav"
            if download_one(filename):
                print(filename, "download!")
                n += 1
            else:
                print("nothing more.")
                return
    
    
    if __name__ == "__main__":
        download_all()
    ```

2. 上面的方法能下，但中途可能会卡

3. 加入请求头，并将其下载入一个文件夹内

    ```python
    from requests import get
    
    
    def download_one(filename):
        url = "http://www.pythonchallenge.com/pc/hex/" + filename
        res = get(url, auth=("butter", "fly"))
        if res.ok:
            f = open(filename, "wb")
            f.write(res.content)
            f.close()
            return True
        else:
            return False
    
    
    def download_all():
        n = 1
        while True:
            filename = f"lake{n}.wav"
            if download_one(filename):
                print(filename, "download!")
                n += 1
            else:
                print("nothing more.")
                return
    
    
    if __name__ == "__main__":
        download_all()
    ```

4. 如果中途还是卡了，可以关闭程序，修改循环起始数据，继续下载

### part2

1. 随机听几个音频，比较刺耳

2. 右键查看一下属性，发现其大小为 `10,844 bytes`

3. 从第 19 题学到：`.wav` 的文件头大小为 `44 bytes`

4. 拿 Python 的交互环境当一下计算器

    ```python
    >>> from math import sqrt
    >>> sqrt((10844 - 44) // 3)  # 每个颜色三个字节
    60.0
    >>> 
    ```

5. 可以大胆猜测每个音频均可化为 60x60 的图片，然后像题图一样拼成 300x300 的大图

    ```python
    from PIL import Image
    
    filename = "lake1.wav"
    f = open(filename, "rb")
    data = f.read()[44:]
    f.close()
    img = Image.new("RGB", (60, 60))
    img.frombytes(data)
    img.save("lake_01.jpg")
    img.close()
    ```

6. 得到第一张图片

    ![lake01](.\imgs\25_lake_01.jpg)

### part3

1. 生成 25 张图片（不必一一保存），并将其以 5x5 的排列拼成一幅图片

    ```python
    from PIL import Image
    
    
    def wav2img(filename):
        with open(filename, "rb") as f:
            img = Image.new("RGB", (60, 60))
            img.frombytes(f.read()[44:])
            return img
    
    
    def jigsaw_puzzle():
        jigsaw = Image.new("RGB", (300, 300))
        for i in range(25):
            row, col = divmod(i, 5)  # div + mod
            piece = wav2img(f"lake{i+1}.wav")
            jigsaw.paste(piece, (col*60, row*60))
        jigsaw.save("25_result.jpg")
    
    
    if __name__ == "__main__":
        jigsaw_puzzle()
    ```

2. 得到图片

    ![result](.\imgs\25_result.jpg)
    
3. 得到解：`decent`

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/decent.html`