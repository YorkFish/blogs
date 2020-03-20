# 不完全总结

## 第 *1* 题

### 移位密码 translate(xxx.maketrans())

#### 方法一

```python
s = "map"
intab = ''.join([chr(e) for e in range(97, 123)])
outtab = ''.join([chr(97 + (e-97+2) % 26) for e in range(97, 123)])
transtab = str.maketrans(intab, outtab)
print(s.translate(transtab))

>>>
ocr
```

#### 方法二

```python
intab = bytes([i for i in range(ord('a'), ord('z')+1)])
outtab = intab[2:] + intab[:2]
transtab = bytes.maketrans(intab, outtab)
print("map".translate(transtab))

>>>
ocr
```

## 第 *2* 题

### 统计出现次数 collections.Counter

```python
from collections import Counter

print(Counter("abbcdde"))

>>>
Counter({'b': 2, 'd': 2, 'a': 1, 'c': 1, 'e': 1})
```

## 第 *3* 题

### re.findall

```python
from re import findall

print(findall("[a-z][A-Z]{3}([a-z])[A-Z]{3}[a-z]", "aBBBcDDDefGGGhIIIjj"))

>>>
['c', 'h']
```

## 第 *4* 题

### 获取网页内容

#### 方法一 urllib

```python
import urllib.request

response = urllib.request.urlopen("http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345")
html = response.read()
print(html)

>>>
b'and the next nothing is 44827'
```

#### 方法二 requests

```python
from requests import get

response = get("http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345")
print(response.text)

>>>
and the next nothing is 44827
```

### re.findall

```python
from re import findall

print(findall("\d{3,}", "abc 12 34567"))

>>>
['34567']
```

## 第 *5* 题

### “泡菜”

#### pickle.dump

```python
from pickle import dump

text = "Python Challenge"
f = open("test.pkl", "wb")
dump(text, f)
f.close()
```

- 查看 `test.pkl`（有点尴尬）

    > €X   Python Challengeq .

#### pickle.load

```python
from pickle import load

f = open("test.pkl", "rb")
text = load(f)
f.close()
print(text)

>>>
Python Challenge
```

## 第 *6* 题

### 获取压缩包中的 comment 信息

#### zipfile

```python
from zipfile import ZipFile

channel = ZipFile("channel.zip", 'r')

readme = channel.open("readme.txt", 'r')
print(readme.read())
readme.close()

t = channel.getinfo("90052.txt").comment
print(t)
channel.close()

>>>
...  # 省略
b'*'
```

#### bytes to string

```python
s = b"abc"
print(str(s, encoding="utf-8"))
print(bytes.decode(s))

>>>
abc
abc
```

## 第 *7* 题

### 获取图片的像素信息

#### pillow (PIL.Image)

```python
from PIL import Image

img = Image.open("oxygen.png")
pix = img.load()  # 为图像分配存储空间并加载像素数据
print(pix[0, 0])

>>>
(79, 92, 23, 255)
```

#### bytes

```python
# 用法与 str 相似，列出来是因为我以前几乎没用过
print(bytes([1, 2, 3]))
print(list(b'\x01\x02\x03'))

>>>
b'\x01\x02\x03'
[1, 2, 3]
```

## 第 *8* 题

### 解压缩

#### bz2.decompress

```python
from bz2 import decompress

un = b"BZh91AY&SYA\xaf\x82\r\x00\x00\x01\x01\x80\x02\xc0\x02\x00 \x00!\x9ah3M\x07<]\xc9\x14\xe1BA\x06\xbe\x084"
print("un:", decompress(un))

>>>
un: b'huge'
```

## 第 *9* 题

### PIL.Image & PIL.ImageDraw

- `PIL.Image.new(mode, size, color=0)`
    - **mode** –
        - `1` (1-bit pixels, black and white, stored with one pixel per byte)
        - `L` (8-bit pixels, black and white)
        - `P` (8-bit pixels, mapped to any other mode using a color palette)
        - `RGB` (3x8-bit pixels, true color)
        - `RGBA` (4x8-bit pixels, true color with transparency mask)
        - ......
- `PIL.ImageDraw.Draw(im, mode=None)`
    - **im** – The image to draw in.
- `PIL.ImageDraw.ImageDraw.line(xy, fill=None, width=0, joint=None)`
    - **xy** –
        - Sequence of either 2-tuples like `[(x, y), (x, y), ...]`
        - or numeric values like `[x, y, x, y, ...]`.
- `PIL.ImageDraw.ImageDraw.polygon(xy, fill=None, outline=None)`
    - **fill** – Color to use for the fill.

```python
from PIL import Image, ImageDraw

rect1 = [(100, 100), (200, 100), (200, 200), (100, 200), (100, 100)]
rect2 = [300, 100, 400, 100, 400, 200, 300, 200]

img = Image.new("RGB", (500, 500))
draw = ImageDraw.Draw(img)
draw.line(rect1, fill="white")  # 需要首尾相连
draw.polygon(rect2, fill="red")  # 不需首尾相连
img.show()  # 展示
img.save("result.png")  # 保存
```

## 第 *11* 题

### PIL.Image

```python
from PIL import Image

img = Image.open("cave.jpg")
small = img.crop((0, 0, 10, 5))  # 裁剪
big = small.resize((500, 250))  # 放大至 500X250
```

```python
from PIL import Image

img = Image.open("cave.jpg")
w, h = img.size
print(w, h)
print(img.size[0], img.size[1])
print(img.width, img.height)
print(img.mode)

>>>
640 480
640 480
640 480
RGB
```

```python
from PIL import Image

img = Image.open("cave.jpg")
new = Image.new("RGB", (500, 500))

pix = img.getpixel((0, 0))  # 获取点 (0, 0) 的像素值
print(pix)
new.putpixel((0, 0), pix)  # 将像素值 pix 写入 new 的 (0, 0) 点

>>>
(0, 20, 0)
```

## 第 *12* 题

### curl

- 按传统，习惯称 *cURL* 为下载工具，支持的通信协议有许多，*HTTPS* 是其中一种
- 一般用法

```
york$ curl https://www.
...
```

- 需要账号、密码时

```
york$ curl -u username:password https://www.
...
```

### 文件头

```python
img = open("evil2.gfx", "rb")
data = img.read(80)
img.close()

for i in range(5):
    print(bytes(data[i::5]))

>>>
b'\xff\xd8\xff\xe0\x00\x10JFIF\x00\x01\x01\x01\x00\xb4'
b'\x89PNG\r\n\x1a\n\x00\x00\x00\rIHDR'
b'GIF87a@\x01\xf0\x00\xe7\x00\x00\x00\x01\x00'
b'\x89PNG\r\n\x1a\n\x00\x00\x00\rIHDR'
b'\xff\xd8\xff\xe0\x00\x10JFIF\x00\x01\x01\x01\x00\xb4'
```

- 关于格式
    - `JFIF -> jpg`
    - `PNGIHDR -> png`
    - `GIFa -> gif`

## 第 *13* 题

### “通信”

#### xmlrpc.client

```python
>>> from xmlrpc import client
>>> conn = client.ServerProxy("http://www.pythonchallenge.com/pc/phonebook.php")
>>> conn
<ServerProxy for www.pythonchallenge.com/pc/phonebook.php>
>>> conn.system.listMethods()  # 列出方法
['phone', 'system.listMethods', 'system.methodHelp', 'system.methodSignature', 'system.multicall', 'system.getCapabilities']
>>> 
>>> 
>>> conn.system.methodHelp("phone")  # 查看帮助
'Returns the phone of a person'
>>> conn.system.methodSignature("phone")  # 查看使用何种类型的参数
[['string', 'string']]
>>> 
>>>     
>>> conn.phone("Bert")  # call Bert
'555-ITALY'
```

## 第 *15* 题

### “万年历”

#### datetime.datetime

```python
from datetime import datetime

date = datetime(2020, 1, 1)
print(date.year, date.month, date.day)
print(date.weekday())  # 周一至周日依次对应 0, 1, 2, 3, 4, 5, 6

>>>
2020 1 1
2  # 2020-01-01 是周三
```

## 第 *16* 题

### PIL.Image & PIL.ImageChops

```python
from PIL import Image

img = Image.open("mozart.gif")
res = img.histogram()
print(len(res))
print(res[:10])  # 0-255 各个像素值出现的个数

>>>
256
[0, 0, 0, 0, 1, 14, 0, 36, 66, 1684]
```

- `Image.crop(box=None)`
    - **box** – The crop rectangle, as a (left, upper, right, lower)-tuple.

```python
from PIL import Image, ImageChops

img = Image.open("mozart.gif")

box = (0, 0, 640, 1)  # left, upper, right, lower 最后一行不取
row = img.crop(box)  # 裁剪

row2bytes = row.tobytes()
i = bytes.index(195)
row = ImageChops.offset(row, -i)  # 可以看成循环左移 i 个像素

img.paste(row, box)  # 粘贴
```

## 第 *17* 题

### urllib.parse

#### unquote_to_bytes

```python
from bz2 import decompress
from urllib.parse import unquote_to_bytes

with open("17_cookies.txt", 'r') as f:
    text = f.readline()
    res = text.replace('+', ' ')
    ans = unquote_to_bytes(res)
    print(decompress(ans))

>>>
b'is it the 26th already? call his father and inform him that "the flowers are on their way". he\'ll understand.'
```

#### quote, quote_plus

```python
from urllib.parse import quote, quote_plus


print(quote_plus(s))

>>>
123abc%21%40%23%2B%20/
123abc%21%40%23%2B+%2F
```

#### unquote_plus

```python
#!/usr/bin/env python2
# -*- coding: UTF-8 -*-

import bz2
import urllib

s = "BZh91AY%26SY%94%3A%E2I%00%00%21%19%80P%81%11%00%AFg%9E%A0+%00hE%3DM%B5%23%D0%D4%D1%E2%8D%06%A9%FA%26S%D4%D3%21%A1%EAi7h%9B%9A%2B%BF%60%22%C5WX%E1%ADL%80%E8V%3C%C6%A8%DBH%2632%18%A8x%01%08%21%8DS%0B%C8%AF%96KO%CA2%B0%F1%BD%1Du%A0%86%05%92s%B0%92%C4Bc%F1w%24S%85%09%09C%AE%24%90"
data = urllib.unquote_plus(s)
secret = bz2.decompress(data)
print(secret)

>>>
is it the 26th already? call his father and inform him that "the flowers are on their way". he'll understand.
```

### str to bytes

```python
s = "abc"
print(s.encode("utf-8"))
print(bytes(s, "utf-8"))

>>>
b'abc'
b'abc'
```

## 第 *18* 题

### “找茬”

#### difflib & gzip

```python
import difflib
import gzip

data = gzip.open("deltas.gz")
left, right = [], []
for line in data:
    left.append(line[:53].decode()+"\n")  # 这里的回车别忘
    right.append(line[56:].decode())

compare1 = difflib.ndiff(left, right)
compare2 = difflib.Differ().compare(left, right)
```

- compare1 与 compare2 内容一样，均有三种开头
    1. 以 `-` 开头：仅存在于左侧
    2. 以 `+` 开头：仅存在于右侧
    3. 以空格开头：两侧均有

## 第 *19* 题

### base64.b64decode

```python
from base64 import b64decode

s = "UklGRvyzAQBXQVZFZm10IBAAAAABAAEAESsAACJWAAACABAAZGF0YdizAQBABkAMQAtAAEADQAJA"
print(b64decode(s))

>>>
b'RIFF\xfc\xb3\x01\x00WAVEfmt \x10\x00\x00\x00\x01\x00\x01\x00\x11+\x00\x00"V\x00\x00\x02\x00\x10\x00data\xd8\xb3\x01\x00@\x06@\x0c@\x0b@\x00@\x03@\x02@'
```

- `RIFF...` 是 `.wav` 的文件头

### email

```python
import email

message = open("email.txt", "rb").read().decode()  # 将本题注释的所有内容保存为 email.txt
mail = email.message_from_string(message)
audio = mail.get_payload(0).get_payload(decode=True)

f = open("indian.wav", "wb")  # 音频内容：sorry
f.write(audio)
f.close()
```

### wave

- `https://docs.python.org/zh-cn/3/library/wave.html`

```python
import wave

w = wave.open("indian.wav", "rb")
h = wave.open("result.wav", "wb")

print(w.getnchannels())  # 1：单声道
print(w.getsampwidth())  # 2：采样字节长度
print(w.getframerate())  # 11025：采样频率

h.setnchannels(w.getnchannels())
h.setsampwidth(w.getsampwidth()//2)
h.setframerate(w.getframerate()*2)
frames = w.readframes(w.getnframes())  # 读取并返回以 bytes 对象表示的最多 n 帧音频；音频总帧数

wave.big_endiana = 1
h.writeframes(frames)  # 写入音频帧并确保 nframes 是正确的
w.close()
h.close()
```

- `result.wav` 中 `sorry` 与 `You are an idiot` 并存

## 第 *20* 题

### 反复收集 cookie

```python
import requests

# request
url = "http://www.pythonchallenge.com/pc/hex/unreal.jpg"
usr_and_pwd = ("butter", "fly")
res = get(url, auth=usr_and_pwd)  # When the website needs a user name and password
# response
print("Response Status Code:", res.status_code)
print("Response Headers:", res.headers)
print("Size of Content:", len(res.content), "bytes")
print("Content:", repr(res.content[:200]))

>>>
Response Status Code: 200
Response Headers: {'Content-Type': 'image/jpeg', 'Content-Range': 'bytes 0-30202/2123456789', 'Transfer-Encoding': 'chunked', 'Date': 'Sat, 07 Mar 2020 06:52:45 GMT', 'Server': 'lighttpd/1.4.35'}
Size of Content: 30203 bytes
Content: b'\xff\xd8\xff\xe0\x00\x10JFIF\x00\x01\x01\x01\x00H\x00H\x00\x00\xff\...'
```

## 第 *21* 题

### zlib

```python
import zlib

f = open("package.pack", "rb")
data = f.read()
f.close()

data = zlib.decompress(data)
print(data[:6])

>>>
b'x\x9c\x00\x07@\xf8'
```

## 第 *22* 题

### PIL.Image

- `Image.getdata(band=None)`
- `Image.getcolors(maxcolors=256)`
- `Image.getbbox()`

```python
>>> from PIL import Image
>>> gif = Image.open("white.gif")
>>> gif.size
(200, 200)
>>> data = getdata()  # 将此图像的内容作为包含像素值的序列对象返回，可以用 list() 转
>>> len(data)
40000  # 200x200
>>> gif.getcolors()  # 返回此图像中使用过的颜色的列表 [(次数, 颜色值), ...]
[(39999, 0), (1, 8)]
>>> gif.getbbox()  # 计算图像中非零区域的边界框
(100, 100, 101, 101)
>>> gif.seek(1)
>>> gif.getbbox()
(100, 102, 101, 103)
>>> 
```

## 第 *23* 题

### this

```python
import this

s = "va gur snpr bs jung?"
print(''.join([this.d.get(c, c) for c in s]))

>>>
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
...  # 省略若干行
in the face of what?
```

## 第 *25* 题

### requests.Session

```python
import requests


req = requests.Session()  # # 创建一个session对象（跨请求保持某些参数）
header = {"User-Agent": "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.116 YaBrowser/16.10.0.2564 Yowser/2.5 Safari/537.36"}
url = "http://www.pythonchallenge.com/pc/hex/lake1.wav"
res = req.get(url, auth=("butter", "fly"), headers=header)
with open(r"lake\lake1.wav", "wb") as f:  # 需事先在当前文件夹下建好 lake 文件夹
    if res.ok:  # get 到，则返回 True
        f.write(res.content)
```

## 第 *26* 题

### bytearray

```python
>>> s = b"abcdefg"
>>> s[3] = ord('D')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'bytes' object does not support item assignment
>>> 
>>> t = bytearray(s)  # bytearray 可当作 array 那样使用
>>> t[3] = ord('D')
>>> t
bytearray(b'abcDefg')
>>> 
```

### md5

```
york$ md5sum mybroken.zip repaired.zip
bbf6616928e23ecfef4b717f281c53cc *mybroken.zip
bbb8b499a0eef99b52c7f13f4e78c24b *repaired.zip
```

```python
from hashlib import md5

f = open("mybroken.zip", "rb")
data = f.read()
f.close()

print(md5(data).hexdigest())

>>>
bbf6616928e23ecfef4b717f281c53cc
```

## 第 *27* 题

### PIL.Image

- `Image.getpalette()`

```python
>>> from PIL import Image
>>> img = Image.open("zigzag.gif")
>>> colors = img.getpalette()  # 将图像调色板作为列表返回，以 R, G, B 的形式
>>> colors[:9]
[37, 37, 37, 229, 229, 229, 162, 162, 162]
>>> 
```

## 第 *28* 题

### keyword.iskeyword

```python
>>> from keyword import iskeyword
>>> iskeyword("print")
False
>>> iskeyword("if")
True
>>> 
```

## 第 *29* 题

### PIL.Image

- `Image.getbands()`
    - For example, **getbands** on an RGB image returns (“R”, “G”, “B”).

```python
>>> from PIL import Image
>>> img = Image.open("bell.png")
>>> img.getbands()  # 返回一个元组，其中包含此图像中每个标注栏的名称
('R', 'G', 'B')
>>> 
```

## 第 *30* 题

### PIL.Image

- `Image.transpose(method)`
    - **method** – One of
        - `PIL.Image.FLIP_LEFT_RIGHT`
        - `PIL.Image.FLIP_TOP_BOTTOM`
        - `PIL.Image.ROTATE_90`
        - `PIL.Image.ROTATE_180`
        - `PIL.Image.ROTATE_270`
        - `PIL.Image.TRANSPOSE``
        - ``PIL.Image.TRANSVERSE`.

```python
from PIL import Image

img = Image.open("30_result.png")
tmp = img.copy()
tmp = tmp.transpose(Image.ROTATE_90)  # 逆时针旋转 90 度
tmp = tmp.transpose(Image.FLIP_TOP_BOTTOM)  # 上下翻转
```

## 第 *31* 题

### PIL.Image

```python
from PIL import Image

img1 = Image.open("mandelbrot.gif")
img2 = Image.open("mandelbrot_clean.gif")

diff = [(i-j) for i,j in zip(img1.getdata(), img2.getdata()) if i != j]
plot = Image.new('L', (23, 73))  # ‘L’ 比 '1' 暗一些
plot.putdata(diff)
plot.show()
```

## 第 *33* 题

### max

```python
>>> max([])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: max() arg is an empty sequence
>>> max([], default=-1)  # 不常用，但与 dict.get(sth, default) 相似
-1
>>> 
```

