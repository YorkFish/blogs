# 第 *19* 题 *please!*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/hex/bin.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/bin.html</a>

## 2. 题图

![please](.\imgs\19_map.jpg)

## 3. 提示

- 网页源码中有一串很长的注释

    ```txt
    From: leopold.moz@pythonchallenge.com
    Subject: what do you mean by "open the attachment?"
    Mime-version: 1.0
    Content-type: Multipart/mixed; boundary="===============1295515792=="

    It is so much easier for you, youngsters.
    Maybe my computer is out of order.
    I have a real work to do and I must know what's inside!

    --===============1295515792==
    Content-type: audio/x-wav; name="indian.wav"
    Content-transfer-encoding: base64

    ...  # 省略了近 2000 行，方便起见，我将此处信息保存在文件 please.txt

    --===============1295515792==--
    ```

## 4. 解法

### part1

1. 网页的注释像是 `Leopold` 老爷子发过来的一封邮件
2. 他说：`open the attachment?`，说明有个附件
3. `audio/x-wav; name="indian.wav"` 说明附件是一个音频
4. `base64` 提示了编码方式

    ```python
    from base64 import b64decode
    
    f = open("please.txt", "rb")
    audio = open("indian.wav", "wb")
    
    for line in f.readlines():
        audio.write(b64decode(line.strip()))
    
    f.close()
    audio.close()
    ```

5. 音频中仅有一个男声单词 `sorry`

### part2

- 打开网址：`http://www.pythonchallenge.com/pc/hex/sorry.html`，看到
  
    > "what are you apologizing for?"

### part3

1. 音频约 *5* 秒，不该只有一个单词
2. 关于 `wav` 格式的文件头
    - 前 *44* 个字节是固定的
    - 其余的数据分高八位与低八位，高位影响大，低位影响小
3. 试着“翻转高低位”

    ```python
    with open("indian.wav", "rb") as f:
        data = f.read()
        new = open("indian_1.wav", "wb")
        file_head = data[:44]  # 文件头部
        wave_data = data[44:]  # 声音数据
        new.write(file_head)  # 写入头部数据
        new.write(wave_data[::-1])  # 写入反转的声音数据
        new.close()
    ```

4. 打开 `indian_1.wav`，声音变得丰富了，但听不清词

### part4

1. 翻转有误
    - 上面是将 `12345678` 翻转为 `87654321`
    - 应该翻转为 `21436587`
2. 简单地说，除了文件头，其他的数据需要翻转各自的“高八位与低八位”

    ```python
    with open("indian.wav", "rb") as f:
        data = f.read()
        file_head = data[:44]
        wave_data = data[44:]
        tail = []
        for i in range(0, len(wave_data), 2):
            tail.extend([wave_data[i+1], wave_data[i]])
        new = open("indian_2.wav", "wb")
        new.write(file_head)
        new.write(bytes(tail))
        new.close()
    ```

3. 播放 `indian_2.wav`，听到：`You are an idiot. Ha, ha, ha, ...`
4. 关键字：`idiot`

### part5

1. 打开网址：`http://www.pythonchallenge.com/pc/hex/idiot.html`
2. 网页内容
    - 上方：`Leopold` 的肖像
    - 下方：`"Now you should apologize..."` 和 `Continue to the next level`
3. 点击 `Continue to the next level`，去到下一题

### other

- 做一件与本题无关的事：将图中的每个像素改为其“补色”
- 补色的 `R, G, B` 的算法：`255 - color_value`

    ```python
    from PIL import Image
    
    
    def com_color(color):
        r, g, b = color
        return 255-r, 255-g, 255-b
    
    if __name__ == "__main__":
        img = Image.open("19_map.jpg")
        data = map(com_color, img.getdata())
        img.putdata(list(data))
        img.save("19_new_map.jpg")
        img.close()
    ```

- 得到一张清晰的图片

    ![new_map](.\imgs\19_new_map.jpg)

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/idiot2.html`