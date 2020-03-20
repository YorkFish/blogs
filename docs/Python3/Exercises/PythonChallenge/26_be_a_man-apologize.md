# 第 *26* 题 *be a man - apologize!*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/hex/decent.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/decent.html</a>

## 2. 题图

![decent](.\imgs\26_decent.jpg)

## 3. 提示

- 网页内

    > Hurry up, I'm missing the boat

- 网页源码

    > you've got his e-mail
    >
    > Join us at the IRC: irc.freenode.net #pythonchallenge

## 4. 解法

### part1

1. 第 *23* 题开头，我曾给 `Leopold` 老爷子发过一封“道歉信”
2. 第 *24* 题结尾，我从 `maze.zip` 中得到了 `mybroken.zip`，并得知其中有 `mybroken.gif`
3. 回顾一下 `Leopold` 的回信

    > Never mind that.
    >
    > Have you found my broken zip?
    >
    > md5: bbb8b499a0eef99b52c7f13f4e78c24b
    >
    > Can you believe what one mistake can lead to?

4. `Leopold` 大概想说：仅仅一个字节的改变，就会令文件的 `md5` 值发生巨大的变化
5. 可以推断，压缩文件 `mybroken.zip` 被改动了一个字节

### part2

1. 查看压缩包属性，其大小为 `2,701 bytes`（去掉一个字节恰能凑整，可惜不是这条思路）
2. 按暴力破解的方法，每次修改一个字节，直到算出的 `md5` 值与 `Leopold` 给出的一样为止

    ```python
    from hashlib import md5
    
    
    def repair(data, md5str):
        n = len(data)
        for i in range(n):
            t = data[i]
            for byte in range(256):
                data[i] = byte
                if md5(data).hexdigest() == md5str:
                    print("broken because of bytes", i)
                    return True
            data[i] = t
        return False
    
    
    if __name__ == "__main__":
        md5str = "bbb8b499a0eef99b52c7f13f4e78c24b"
        f = open("mybroken.zip", "rb")
        data = bytearray(f.read())
        f.close()
        
        if repair(data, md5str):
            zf = open("repaired.zip", "wb")
            zf.write(data)
            zf.close()
            print("done!")
        else:
            print("faild!")
    
    >>>
    broken because of bytes 1234
    done!
    ```

3. 看一看修改一个字节前后的 `md5` 值

    ![difference](.\imgs\26_difference.png)

### part3

1. 解压缩 `repaired.zip`，得到图片 `mybroken.gif`

    ![mybroken](.\imgs\26_mybroken.gif)

2. 其实使用 `bandzip` 可以直接看到 `speed`，原因可能和第 *12* 题的第四张破损的图片相同
3. 打不开网址 `http://www.pythonchallenge.com/pc/hex/speed.html`
4. 回顾提示语：`I'm missing the boat`
5. 和第 *23* 题的 `this` 一样，这也是双关语，意指 `speed` 漏下了 `boat`
6. 解为  `speedboat`

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/speedboat.html`