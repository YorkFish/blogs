# 第 *18* 题 *can you tell the difference?*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/balloons.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/balloons.html</a>

## 2. 题图

![balloons](.\imgs\18_balloons.jpg)

## 3. 提示

- 网页源码注释

    > it is more obvious that what you might think

## 4. 解法

### part1

1. 图中左右区别在“亮度”——`brightness`
    - 若以 `bright` 试之，会得到 `ness`，其意也为 `brightness`
2. 打开网页：`http://www.pythonchallenge.com/pc/return/brightness.html`
    - 网页源码中有一句注释：`maybe consider deltas.gz`
3. 将地址改为：`http://www.pythonchallenge.com/pc/return/deltas.gz`
    - 可下载得到文件 `deltas.gz`
4. 解压后，得到`delta.txt`
    - 建议用记事本以外的编辑器打开，那样看得清楚

### part2

1. 开头八组数据为：`89 50 4e 47 0d 0a 1a 0a`，有了第 *12* 题和第 *7* 题的经验，可大胆猜测其为“十六进制”，且与 `ASCII` 码有关

    ```python
    >>> hex_nums = "89 50 4e 47 0d 0a 1a 0a".split()
    >>> dec_nums = [int(e, 16) for e in hex_nums]
    >>> bytes(dec_nums)
    b'\x89PNG\r\n\x1a\n'
    >>> 
    ```

2. 看到 `\x89PNG` 等字样，可以判断这串数据是 `.png` 格式的文件头
3. 第 *51* 行开始，左右出现不同，且该行右边等于该行下一行的左边
4. 第 *56* 行开始，左右在隔几行时，仍会出现相同的情况

### part3

1. 需要将数据分成三组
    1. 只存在于左侧
    2. 两侧均存在
    3. 只存在于右侧
2. 自己造轮子也费不了几行，不过有现成的 `difflib` 可用

    ```python
    import difflib
    import gzip
    
    data = gzip.open("deltas.gz")
    left, right = [], []
    for line in data:
        left.append(line[:53].decode()+"\n")  # 这里别忘
        right.append(line[56:].decode())
    
    compare = difflib.ndiff(left, right)
    
    fl = open("18_left.png", "wb")  # only in left
    fb = open("18_both.png", "wb")  # both have
    fr = open("18_right.png", "wb")  # only in right
    
    for line in compare:
        bs = bytes([int(e, 16) for e in line[2:].strip().split() if e])
        if line[0] == '-':
            fl.write(bs)
        elif line[0] == '+':
            fr.write(bs)
        else:
            fb.write(bs)
    
    fl.close()
    fb.close()
    fr.close()
    ```

3. 图 *left*

    ![left](.\imgs\18_left.png)

4. 图 *both*

    ![botht](.\imgs\18_both.png)

5. 图 *right*

    ![right](.\imgs\18_right.png)

### part4

1. `../hex/bin.html` 应该是说下一关地址为：`http://www.pythonchallenge.com/pc/hex/bin.html`
2. 打开网址后，类似第 *8* 题，需要账号、密码（看来，做后续的题目要更新密码了）
3. `butter` 与 `fly` 可以凑成 `butterfly`，按顺序正好
    - 账号：`butter`
    - 密码：`fly`

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/bin.html`