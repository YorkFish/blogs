# 第 *30* 题 *relax you are on 30*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/ring/yankeedoodle.html" target="_blank">>>> http://www.pythonchallenge.com/pc/ring/yankeedoodle.html</a>

## 2. 题图

![yankeedoodle](.\imgs\30_yankeedoodle.jpg)

## 3. 提示

- 网页内

    > The picture is only meant to help you relax

- 网页源码注释

    > while you look at the csv file

## 4. 解法

### part1

1. 题图是作者让我们放松心情的
2. 至于 `csv`，按照惯例，将网址后缀改为 `csv`，如此可以下载到文件 `yankeedoodle.csv`
3. 可以使用 `Excel` 打开看看，都是数字
4. 使用 *Python* 算一下数据数量

    ```python
    >>> f = open("yankeedoodle.csv")
    >>> nums = [num.strip() for num in f.read().split(',')]
    >>> len(nums)
    7367
    >>> 
    ```

5. 将 `7367` 分解质因数

    ```python
    def prime_factorization(num):
        factor = []
        for i in range(3, int(num**0.5), 2):
            if num % i == 0:
                factor.append(i)
                factor.append(num // i)
        print(factor)
    
    
    if __name__ == "__main__":
        prime_factorization(7367)
    
    >>>
    [53, 139]
    ```

6. *53* 与 *139* 正好可以作为 `width` 或 `height`
7. 经检验，`w = 53, h = 139`

### part2

1. 将数据转换成 `53X139` 的图像

    ```python
    from PIL import Image
    
    f = open("yankeedoodle.csv")
    nums = [float(num.strip()) for num in f.read().split(',')]
    
    img= Image.new('P', (53, 139))
    img.putdata(nums, 256)
    img.save("30_result.png")
    ```

2. 得到一张图片

    ![result](.\imgs\30_result.png)

### part3

1. 图片需要翻转一下

    ```python
    from PIL import Image
    
    img = Image.open("30_result.png")
    tmp = img.copy()
    tmp = tmp.transpose(Image.ROTATE_90)  # 逆时针旋转 90 度
    tmp = tmp.transpose(Image.FLIP_TOP_BOTTOM)  # 上下翻转转
    tmp.save("30_result2.png")
    ```

2. 得到正常视角的图片

    ![result2](.\imgs\30_result2.png)

### part4

1. 按上图的公式做

    ```python
    f = open("yankeedoodle.csv")
    nums = [num.strip() for num in f.read().split(',')]
    f.close()
    res = [int(x[0][5] + x[1][5] + x[2][6]) for x in zip(nums[0::3], nums[1::3], nums[2::3])]
    print(''.join([chr(e) for e in res]))
    
    >>>
    So, you found the hidden message.
    There is lots of room here for a long message, but we only need very little space to say "look at grandpa", so the rest is just garbage.
    VTZ.l'tf*Om@I"p]#R`cWEBZ40ofSC>OZFkRP0\)+b?Ir)S%Jt3f{ei%n2<FErFx~IzVm JTh =xdx++'de8C5'|>2\/We;ib(b%d$N<2u(o$*d@.*6Fd'nW5#J!}a]T"1Q-7Y~bOF]T+^9d]e^J^=&I&<x|EEgdQ$$pX'f!_n>F0...
    ```

2. 关键字：`grandpa`
3. 之后的 *gibberish* 都可以忽略

## 5. 答案

- `http://www.pythonchallenge.com/pc/ring/grandpa.html`