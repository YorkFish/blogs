# 第 *24* 题  *from top to bottom*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/hex/ambiguity.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/ambiguity.html</a>

## 2. 图片

![maze](.\imgs\24_maze.png)

## 3. 提示

- 无

## 4. 解法

### part1

1. 将图片放大后，会发现这是一张巨大的“迷宫图”
2. 标题说 `from top to bottom`，说明入口在上方，出口在下方
3. 一开始，我下意识地认为黑色的是墙，实际上，黑色的是路径
4. 此外，仔细看还能发现：路径并非完全是黑色，中间还混一些“红点”
5. 放大图片可以发现入口在右上角

    ![in](.\imgs\24_maze_in.png)

6. 出口在左下角

    ![out](.\imgs\24_maze_out.png)

7. 当然，使用 Python 解得入口与出口更有说服力

    ```python
    >>> from PIL import Image
    >>> maze = Image.open("maze.png")
    >>> w, h = maze.size
    >>> w, h
    (641, 641)
    >>> for i in range(w): print(maze.getpixel((i, 0)))
    ...  # 省去 638 个 (255, 255, 255, 255)
    (255, 255, 255, 255)
    (0, 0, 0, 255)  # 入口，第一行，倒数第二个像素
    (255, 255, 255, 255)
    >>> for i in range(w): print(maze.getpixel((i, h - 1)))
    (255, 255, 255, 255)
    (0, 0, 0, 255)  # 出口，最后第一行，第二个像素
    (255, 255, 255, 255)
    ...  # 省去 638 个 (255, 255, 255, 255)
    >>> 
    ```

### part2

- 使用 *BFS* 从出口反推路径，并绘制出路线（也有别的方法，比如 A-Star）

    ```python
    from PIL import Image
    
    
    def find_way(img, entrance, export):
        w, h = img.size
        pix = img.load()
        right_way={}
        trial = [export]
        white = (255, 255, 255, 255)
        direction = [(-1,0), (1,0), (0,-1), (0,1)]  # 第 14 题的方法二也是这种思路，但顺序不同
        try:
            while True:
                t = trial.pop(0)
                if t == entrance:
                    print("Find over!")
                    print(len(right_way))
                    break
                for d in direction:
                    new = (t[0]+d[0], t[1]+d[1])
                    if -1 < new[0] < w and -1 < new[1] < h:
                        if pix[new[0],new[1]] != white and new not in right_way:
                            trial.append(new)
                            right_way[new] = t
            return right_way
        except Exception as e:
            print(e)
    
    
    def reproduce(img, way, entrance, export):
        new_img = img.copy()
        t = (0, 255, 0, 255)  # green
        if way:
            p = entrance
            while p != export:
                new_img.putpixel(p, t)
                p = way[p]
            new_img.putpixel(p, t)
        new_img.save("24_maze_route.png")
    
    
    if __name__ == "__main__":
        img = Image.open("maze.png")
        entrance = (639, 0)
        export = (1, 640)
    
        way = find_way(img, entrance, export)
        reproduce(img, way, entrance, export)
    ```

2. 得到图片

    ![maze_route](.\imgs\24_maze_route.png)

### part3

1. 黑色的像素点值是 0，这样的点都是在路径的偶数点 (0, 2, ...)

2. 查看非黑色像素点的值，即路径数为奇数的点的像素值

    ```python
    >>> maze.getpixel((639, 1))  # 入口的下一个点
    (80, 0, 0, 255)
    >>> maze.getpixel((639, 3))
    (75, 0, 0, 255)
    >>> chr(80)
    'P'
    >>> chr(75)
    'K'
    >>> 
    ```

3. 发现以 `PK` 开头，有了第 20 题的经验，可知这是 `zip` 格式的文件头

4. 将这些数据写入

    ```python
    from PIL import Image
    
    
    def find_way(w, h, pix, entrance, export):
        right_way={}
        trial = [export]
        white = (255, 255, 255, 255)
        direction = [(-1,0), (1,0), (0,-1), (0,1)]
        try:
            while True:
                t = trial.pop(0)
                if t == entrance:
                    print("Find over!")
                    # print(len(right_way))  # 194941
                    break
                for d in direction:
                    new = (t[0]+d[0], t[1]+d[1])
                    if -1 < new[0] < w and -1 < new[1] < h:
                        if pix[new[0],new[1]] != white and new not in right_way:
                            trial.append(new)
                            right_way[new] = t
            return right_way
        except Exception as e:
            print(e)
    
    
    def reproduce(pix, way, entrance, export):
        t = (0, 255, 0, 255)
        if way:
            p = entrance
            data = []
            while p != export:
                data.append(pix[p[0],p[1]][0])
                p = way[p]
    
        with open("maze.zip", "wb") as f:
            f.write(bytes(data[1::2]))  # 黑色的像素点值是0，而且都是在偶数字节
    
    
    if __name__ == "__main__":
        img = Image.open("maze.png")
        w, h = img.size
        pix = img.load()
        entrance = (639, 0)
        export = (1, 640)
    
        way = find_way(w, h, pix, entrance, export)
        reproduce(pix, way, entrance, export)
    ```

5. 得到一个压缩包
6. 解压后有一张图片（如下）和另一个名为 `mybroken.zip` 的压缩包

    ![maze](.\imgs\24_maze.jpg)

7. `lake` 为解

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/lake.html`