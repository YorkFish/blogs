# 第 *21* 题 *dealing package.pack*

## 1. 地址

- 无

## 2. 文件

1. `readme.txt`
2. `package.pack`

## 3. 提示

- `readme.txt`中的信息如下

    > Yes! This is really level 21 in here. 
    > And yes, After you solve it, you'll be in level 22!
    >
    > Now for the level:
    >
    > * We used to play this game when we were kids
    > * When I had no idea what to do, I looked backwards.

## 4. 解法

### part1

1. 使用“十六进制编辑器”打开 `readme.txt`
2. 搜索得知：`78 9c 00 0a`  为 `zlib` 文件头，此外还搜得
    - `gzip: 1f 8b 08`
    - `lzma: 6c 00`
3. 至于“小时候玩的游戏”，有人说是“击鼓传花”，我感觉像“套娃”

### part2

1. 慢慢来，多试几次

    ```python
    >>> import zlib
    >>> f = open("package.pack", "rb")
    >>> data = f.read()
    >>> data[:6]
    b'x\x9c\x00\n@\xf5'
    >>> data = zlib.decompress(data)
    >>> data[:6]
    b'x\x9c\x00\x07@\xf8'
    >>> data = zlib.decompress(data)
    >>> data[:6]
    b'x\x9c\x00\x06@\xf9'
    >>> data = zlib.decompress(data)
    >>> data[:6]
    b'x\x9c\x00\xff?\x00'
    >>> data = zlib.decompress(data)
    >>> data[:6]
    b'x\x9c\x00\xff?\x00'
    >>> data = zlib.decompress(data)
    >>> data[:6]
    b'x\x9c\x84vuT'
    >>> data = zlib.decompress(data)
    >>> data[:6]
    b'BZh91A'
    >>>
    ```

2. 上方使用 `zlib.decompress(data)` 六次后，`data` 的“文件头”变为了 `BZh`
3. 改使用 `Bz2`

    ```python
    >>> import bz2  # 接着上面的程序
    >>> data = bz2.decompress(data)
    >>> data[:6]
    b'BZh91A'
    >>> data = bz2.decompress(data)
    >>> data[:6]
    b'BZh91A'
    >>> data = bz2.decompress(data)
    >>> data[:6]
    b'x\x9c\x00\x1f@\xe0'
    >>> 
    ```

4. 上方使用 `bz2.decompress(data)` 三次后又回到 `zlib` 了
5. 加速，让 `while` 处理

    ```python
    >>> while True:
    ...   if data.startswith(b'x\x9c'):
    ...     data = zlib.decompress(data)
    ...   elif data.startswith(b'BZh'):
    ...     data = bz2.decompress(data)
    ...   else:
    ...     break
    ...
    >>> len(data)
    184947
    >>> data[:6]
    b'\x80\x8d\x96\xcb\xb5r'
    >>> 
    ```

### part3

1. 回想提示：`When I had no idea what to do, I looked backwards.`
2. 做一次 `reverse`

    ```python
    >>> data = data[::-1]
    >>> data[:6]
    b'x\x9c\x00\x0c@\xf3'
    >>> 
    ```

3. 看来，总共三种操作：`zlib.decompress, bz2.decompress, reverse`

    ```python
    import bz2
    import zlib
    
    with open("package.pack", "rb") as f:
        data = f.read()
        
        while True:
            if data.startswith(b'x\x9c'):
                data = zlib.decompress(data)
            elif data.startswith(b'BZh'):
                data = bz2.decompress(data)
            elif data.endswith(b'\x9cx'):  # \x9c 是一个，x 是一个
                data = data[::-1]
            else:
                break
        
        print(data)
    
    >>>
    b'sgol ruoy ta kool'
    ```

4. 这回可以肉眼反转：`look at your logs`

### part4

1. 按 *part3* 的提示，记录 `zlib.decompress` 与 `bz2.decompress` 与 `data[::-1]` 的次数

    ```python
    import bz2
    import zlib
    
    with open("package.pack", "rb") as f:
        data = f.read()
    
    cnt_zlib = cnt_bz2 = cnt_reverse = 0
    while True:
        if data.startswith(b'x\x9c'):
            data = zlib.decompress(data)
            cnt_zlib += 1
        elif data.startswith(b'BZh'):
            data = bz2.decompress(data)
            cnt_bz2 += 1
        elif data.endswith(b'\x9cx'):
            data = data[::-1]
            cnt_reverse += 1
        else:
            break
    print(cnt_zlib, cnt_bz2, cnt_reverse)
    ```

2. 发现反转只做了 *9* 次

3. 将每次操作记录到列表中

    ```python
    import bz2
    import zlib
    
    with open("package.pack", "rb") as f:
        data = f.read()
    
    res = []
    while True:
        if data.startswith(b'x\x9c'):
            data = zlib.decompress(data)
            res.append("zlib")  # 因为不清晰，下一步改为 res.append('z')
        elif data.startswith(b'BZh'):
            data = bz2.decompress(data)
            res.append("bz2")  # 因为不清晰，下一步改为 res.append('b')
        elif data.endswith(b'\x9cx'):
            data = data[::-1]
            res.append("reverse")  # 因为稀有，猜测是 9 行的字符画，改为 \n，下一步把 list 改为 str
        else:
            break
    print(res)
    ```

4. 对上一步，按注释改过后，可看出大致轮廓

5. 再小改一番

    ```python
    import bz2
    import zlib
    
    result = ""
    with open("package.pack", "rb") as f:
        data = f.read()
        while True:
            if data.startswith(b'x\x9c'):
                data = zlib.decompress(data)
                result += ' '
            elif data.startswith(b'BZh'):
                data = bz2.decompress(data)
                result += '#'
            elif data.endswith(b'\x9cx'):
                data = data[::-1]
                result += '\n'
            else:
                break
    print(result)
    
    >>>
          ###          ###      ########    ########    ##########  ########
        #######      #######    #########   #########   #########   #########
       ##     ##    ##     ##   ##      ##  ##      ##  ##          ##      ##
      ##           ##       ##  ##      ##  ##      ##  ##          ##      ##
      ##           ##       ##  #########   #########   ########    #########
      ##           ##       ##  ########    ########    ########    ########
      ##           ##       ##  ##          ##          ##          ##   ##
       ##     ##    ##     ##   ##          ##          ##          ##    ##
        #######      #######    ##          ##          #########   ##     ##
          ###          ###      ##          ##          ##########  ##      ##
    ```

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/copper.html`