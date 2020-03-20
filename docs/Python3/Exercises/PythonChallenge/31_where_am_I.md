# 第 *31* 题 *Where am I?*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/ring/grandpa.html" target="_blank">>>> http://www.pythonchallenge.com/pc/ring/grandpa.html</a>

## 2. 图片

![grandpa](.\imgs\31_grandpa.jpg)

## 3. 提示

- 网页源码注释

    > short break, this ***REALLY*** has nothing to do with Python

## 4. 解法

### part1

1. 点击图片，有提示 `"island : country"`
    - 看来，又要更换账号、密码了
    - 而且，账号是岛屿名称，密码是国家名称
2. 作者说这里的操作与 Python 的关系不大，那就使用百度识图吧
    - 岛屿：苏梅岛 `kohsamui`
    - 国家：泰国 `thailand`

### part2

1. 输入账号、密码后，来到 `http://www.pythonchallenge.com/pc/rock/grandpa.html`
2. 新的标题：`UFOs ?`
3. 新的题图

    ![UFO](.\imgs\31_mandelbrot.gif)

3. 新的提示语

    > That was too easy. You are still on 31...

4. 网页源码中有一段非注释在假装 `HTML` 语句

    ```txt
    <window left="0.34" top="0.57" width="0.036" height="0.027"/>
    <option iterations="128"/>
    ```

### part3

1. 图片看着像“科赫雪花”，不过图片被命名为 `mandelbrot`
2. 搜索得知此为：`mandelbrot 图`
3. 将图片放大，会发现图片中有许多点被改动过

    ![dot](.\imgs\31_dot.png)

### part4

1. 自己生成一张 `mandelbrot` 图，对比新题图
2. `left, top, width, height`，是计算的界限（top 有争议）
3. 经典图如下
   
    ![classic](.\imgs\31_mandelbrot_full.png)

4. 关于上图的说明
    - 原点大约在图中的 `O` 处
    - `left` 等四个数字框住的范围大约在图中右上角的方框处
5. 在二维图像 `(x，y)` 中的每个像素都唯一地对应一个复数 `c`
    - 其实部为 `left + x * width/img_size_w`
    - 其虚部为 `top + y * height/img_size_h`

### part5

1. `z = 0 + 0j`
2. 重复计算 `z = z * z + c`
3. 如果 `z` 收敛，则显示这个像素

    ```python
    from PIL import Image
    
    left, top = 0.34, 0.57  # 0.34 + 0.57i
    width, height = 0.036, 0.027
    iterations = 128
    img1 = Image.open("mandelbrot.gif")
    w, h = img1.size
    rx, ry = width/w, height/h
    
    res = []
    for y in range(h-1, -1, -1):  # 貌似 0.57 是 bottom，作者误写成了 top，故应从下往上走
        for x in range(w):
            c = complex(left + x*rx, top + y*ry)
            z = 0 + 0j
            for i in range(iterations):
                z = z*z + c
                if abs(z) > 2:
                    break
            res.append(i)
    
    img2 = img1.copy()
    img2.putdata(res)
    img2.save("31_mandelbrot_clean.gif")
    ```

4. 得到图像

    ![clean](.\imgs\31_mandelbrot_clean.gif)

### part6

1. 找出不同点

    ```python
    from PIL import Image
    
    img1 = Image.open("mandelbrot.gif")
    img2 = Image.open("newMandelbrot.gif")
    
    diff = [(i-j) for i,j in zip(img1.getdata(), img2.getdata()) if i != j]
    print(len(diff))  # 这些点的绝对值均是 16
    
    >>>
    1679
    ```

2. 分解质因数

    ```python
    def prime_factorization(num):  # level 30 用过
        factor = []
        for i in range(3, int(num**0.5), 2):
            if num % i == 0:
                factor.append(i)
                factor.append(num // i)
        print(factor)
    
    
    if __name__ == "__main__":
        prime_factorization(1679)
    
    >>>
    [23, 73]
    ```

3. 经检验， `w = 23, h = 73` 时可成图

    ```python
    from PIL import Image
    
    img1 = Image.open("mandelbrot.gif")
    img2 = Image.open("newMandelbrot.gif")
    
    diff = [(i-j) for i,j in zip(img1.getdata(), img2.getdata()) if i != j]
    plot = Image.new('L', (23, 73))  # ‘L’ 比 '1' 暗一些
    plot.putdata(diff)
    plot.save("plot.gif")
    ```

4. 得到一张单色图

    ![plot](.\imgs\31_plot.gif)

5. 此图为“阿雷西博信息” `arecibo`

    > In 1974, the Arecibo Message[1] was sent into space via radio-waves from the Arecibo Observatory.

6. 题外话：《三体》中，叶文洁在 *1971* 年也做过差不多的事。。。怪不得新标题是 `UFO ?`

## 5. 答案

- `http://www.pythonchallenge.com/pc/rock/arecibo.html`