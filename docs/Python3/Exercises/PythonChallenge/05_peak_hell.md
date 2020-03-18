# 第 *5* 题 *peak hell*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/def/peak.html" target="_blank">>>> http://www.pythonchallenge.com/pc/def/peak.html</a>

## 2. 图片

![peakhell](.\imgs\05_peakhell.jpg)

## 3. 提示

- 网页内
  
    > pronounce it
- 网页源码注释
  
    > peak hell sounds familiar ?

## 4. 解法

1. 网页源码中除了一条注释，还有一个名为 `banner.p` 的源文件可阅（个人建议复制地址至 `Edge` 下载）

2. 将网页标题 `peak hell` 读快一点，发现像 `pickle`

3. 使用 `pickle` 对 `banner.p` 解密

    ```python
    from pickle import load

    with open("banner.p", "rb") as f:
        print(load(f))

    >>>
    [[(' ', 95)], [(' ', 14), ('#', 5), (' ', 70), (...
    ```

4. 输出的是二维列表，第二维列表中各有 1 至 n 个二元组不等

5. 每个第二维的列表都可以形成一行字符串，所有的行又可以组成一段

    ```python
    from pickle import load
    
    with open("banner.p", "rb") as f:
        res = [''.join(i*j for i, j in line) for line in load(f)]
        print('\n'.join(res))
    ```

- 输出的是一张字符画

    ![channel](.\imgs\05_channel.png)

## 5. 答案

- `http://www.pythonchallenge.com/pc/def/channel.html`