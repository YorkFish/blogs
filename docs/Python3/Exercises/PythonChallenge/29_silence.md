# 第 *29* 题 *silence!*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/ring/guido.html" target="_blank">>>> http://www.pythonchallenge.com/pc/ring/guido.html</a>

## 2. 题图

![whoisit](.\imgs\29_whoisit.jpg)

## 3. 提示

- 网页源码注释：没有注释，但其中 *73* 行空行

## 4. 解法

### part1

1. 图中有许多玻璃制品，于是，将网址末尾改为 `glass`
2. 进入 `http://www.pythonchallenge.com/pc/ring/glass.html` 后，得到

    > yes. this is a glass.

### part2

1. 之前在网上见到有人在论文末尾加入文字并将其改为白色以凑字数，此处有异曲同工之妙
2. 我试着从下往上选择，没想到有“内容”（其实是空格），我将其复制下来，保存在文件 `silence.txt`
3. 既然都是空格，那么大概率与空格的数量有关

    ```python
    f = open("silence.txt")
    lst = []
    for i in range(73):
        lst.append(len(f.readline().rstrip('\n')))
    print(bytes(lst))
    f.close()
    
    >>>
    b'BZh91AY&SY\xd9\xc2p\x18\x00\x00\x04\x9d\x80`\x80\x00\x00\x80 ./\x9c  \x001L\x98\x99\x06F\x112hd\x06jUd\xb9\x9e\xc6\x18\xc5\x92RH\xe5Z"\x01\xba\xa7\x80\x7f\x8b\xb9"\x9c(Hl\xe18\x0c\x00\x00'
    ```

### part3

1. 使用 `bz2` 解压缩

    ```python
    from bz2 import decompress
    
    f = open("silence.txt")
    lst = []
    for i in range(73):
        lst.append(len(f.readline().rstrip('\n')))
    f.close()
    
    t = bytes(lst)
    print(decompress(t))
    
    >>>
    b"Isn't it clear? I am yankeedoodle!"
    ```

2. 关键字：`yankeedoodle`
3. 搜索得知：扬基·杜德尔又叫扬基曲、扬基小调

## 5. 答案

- `http://www.pythonchallenge.com/pc/ring/yankeedoodle.html`