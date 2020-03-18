# 第 *6* 题 *now there are pairs*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/def/channel.html" target="_blank">>>> http://www.pythonchallenge.com/pc/def/channel.html</a>

## 2. 图片

![channel](.\imgs\06_channel.jpg)

## 3. 提示

- 网页内
    - 图片正下方有个 <kbd>PayPal-Donate</kbd> 的 Button
    - 这与解迷无关，是用于“打赏”作者的

- 网页源码注释

    > <-- zip

## 4. 解法

### part1

1. 图中主角是“拉链”，即 `zip`
2. 网页源码第一行，`<html> <!-- <-- zip -->`，暗示将 `html` 改为 `zip`
3. 改地址后可下载到 `channel.zip`
4. 解压可得近千个文件，其他均以数字命名，除了 `readme.txt`
5. 查看 `readme.txt`

    > welcome to my zipped list.
    >
    > hint1: start from 90052
    > hint2: answer is inside the zip

6. `90052.txt` 中写着

    > Next nothing is 94191

7. 由此可见，此题与第 4 题类似，只是载体不同

### part2

- 查找文件中的信息

    ```python
    filename = "90052"
    while filename.isdecimal():
        f = open(filename+".txt")
        line = f.readline()
        f.close()
        filename = line.split()[-1]
    print(line)

    >>>
    Collect the comments.
    ```

### part3

1. 使用 `zipfile` 获取 `comment` 信息

    ```python
    from zipfile import ZipFile

    comments = []
    filename = "90052"
    channel = ZipFile("channel.zip", 'r')
    while filename.isdigit():
        filename += ".txt"
        f = channel.open(filename, 'r')
        line = f.readline()
        f.close()
        t = channel.getinfo(filename).comment
        comments.append(str(t, encoding="utf-8"))  # bytes -> str
        filename = bytes.decode(line.split()[-1])  # bytes -> str
    print(comments)

    >>> 
    ['*', '*', '*', ...
    ```

2. 把上方程序的最后一句改为 `print(''.join(comments))` 即可看到（准）答案

    ```txt
    ****************************************************************
    ****************************************************************
    **                                                            **
    **   OO    OO    XX      YYYY    GG    GG  EEEEEE NN      NN  **
    **   OO    OO  XXXXXX   YYYYYY   GG   GG   EEEEEE  NN    NN   **
    **   OO    OO XXX  XXX YYY   YY  GG GG     EE       NN  NN    **
    **   OOOOOOOO XX    XX YY        GGG       EEEEE     NNNN     **
    **   OOOOOOOO XX    XX YY        GGG       EEEEE      NN      **
    **   OO    OO XXX  XXX YYY   YY  GG GG     EE         NN      **
    **   OO    OO  XXXXXX   YYYYYY   GG   GG   EEEEEE     NN      **
    **   OO    OO    XX      YYYY    GG    GG  EEEEEE     NN      **
    **                                                            **
    ****************************************************************
     **************************************************************
    ```

3. 登入 `http://www.pythonchallenge.com/pc/def/hockey.html`，可在新网页得到一句话

    > it's in the air. look at the letters.

4. 检查上方的 *HOCKEY*，可以发现这些字母分别由 `O, X, Y, G, E, N` 组成，“氧气”也正符合上面的提示

## 5. 答案

- `http://www.pythonchallenge.com/pc/def/oxygen.html`