# 第 *32* 题 *etch-a-scetch*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/rock/arecibo.html" target="_blank">>>> http://www.pythonchallenge.com/pc/rock/arecibo.html</a>

## 2. 图片

- 准确地说，这一题的网页中显示的不是图片
- 更像是用 `Js` 写的小游戏

![arecibo](.\imgs\32_arecibo.png)

## 3. 提示

- 网页内

    > Fill in the blanks

- 网页源码
    > you are in level 32
    >
    > for warmup.txt

## 4. 解法

### part1

1. 进入 `http://www.pythonchallenge.com/pc/rock/warmup.txt`

2. 得到

    ```txt
    # Dimensions
    9 9
    
    # Horizontal
    2 1 2
    1 3 1
    5
    
    7
    9
    3
    
    2 3 2
    2 3 2
    2 3 2
    
    # Vertical
    2 1 3
    1 2 3
    3
    
    8
    9
    8
    
    3
    1 2 3
    2 1 3
    ```

3. 看文件名，这应该是热身题

### part2

- 这是一种名为 `Nonograms` 的游戏，从纵向数据看，左右很有可能是对称的

1. 凑横向的 `232`

    ![01](.\imgs\32_01.png)

2. 填上纵横唯一的 `9`

    ![02](.\imgs\32_02.png)

3. 填纵向的两个 `8`

    ![03](.\imgs\32_03.png)

4. 此时横向第 6 行已满，补纵向的第 3 列与第 7 列的 `3`

    ![04](.\imgs\32_04.png)

5. 此时横向第三行已满
    - 此时的第 4 行只有一种填法
    - 若第 4 行定下，则第 1 列与第 9 列也只有一种填法
    - 如此，最后两个也就定了
    
6. 最终效果

    ![05](.\imgs\32_05.png)

### part3

1. 图像是向上的箭头，故关键字为 `up`

2. 更改地址：`http://www.pythonchallenge.com/pc/rock/up.html`，得到

    > You want to go up? Let's scale <u>this</u> up then. Now get serious and solve this.

3. 点击 <kbd>this</kbd> 可以去到 `http://www.pythonchallenge.com/pc/rock/up.txt` 看到新的题目

    ```txt
    # Dimensions
    32 32
    
    # Horizontal lines
    3 2
    8
    10
    3 1 1
    
    5 2 1
    5 2 1
    4 1 1
    15
    
    19
    6 14
    6 1 12
    6 1 10
    
    7 2 1 8
    6 1 1 2 1 1 1 1
    5 1 4 1
    5 4 1 4 1 1 1
    
    5 1 1 8
    5 2 1 8
    6 1 2 1 3
    6 3 2 1
    
    6 1 5
    1 6 3
    2 7 2
    3 3 10 4
    
    9 12 1
    22 1
    21 4
    1 17 1
    
    2 8 5 1
    2 2 4
    5 2 1 1
    5
    
    # Vertical lines
    5
    5
    5
    3 1
    
    3 1
    5
    5
    6
    
    5 6
    9 5
    11 5 1
    13 6 1
    
    14 6 1
    7 12 1
    6 1 11 1
    3 1 1 1 9 1
    
    3 4 10
    8 1 1 2 8 1
    10 1 1 1 7 1
    10 4 1 1 7 1
    
    3 2 5 2 1 2 6 2
    3 2 4 2 1 1 4 1
    2 6 3 1 1 1 1 1
    12 3 1 2 1 1 1
    
    3 2 7 3 1 2 1 2
    2 6 3 1 1 1 1
    12 3 1 5
    6 3 1
    
    6 4 1
    5 4
    4 1 1
    5
    ```

### part4

- 徒手解 `32x32` 的数图，就比较伤身体了
- 思路
    1. 递归地获取每行/列的所有组合方式
    2. 若某一行/列的所有组合中，某一点的值不变，则这一点可以被确定
    3. 用行/列中的确定点去筛选掉列/行中不符合该点值的组合
    4. 反复筛选，直到剩下唯一的组合（作者凑好的）

```python
def get_data(filename):
    """ 获取大小、横/纵向组合方式 """
    f = open(filename)
    flag = -1
    size, hor, ver = [], [], []
    data = [size, hor, ver]
    for line in f:
        if line[0] == '#':
            flag += 1
        elif line[0] == '\n':
            pass
        else:
            data[flag].append(list(map(int, line.split())))
    return data


def get_candidates(nums, size):
    ''' 给出行/列的组合方式，递归地获得所有的排列，# 为选择标记 '''
    n = len(nums)
    candidates = []
    length = size - sum(nums) - (n-1)
    for i in range(length+1):
        head = ' '*i + '#'*nums[0]
        len_h = len(head)
        if n == 1:
            tail = ' ' * (size-len_h)
            candidates.append(head+tail)
        else:
            tails = [' '+j for j in get_candidates(nums[1:], size-len_h-1)]
            candidates.extend([head+tail for tail in tails])
    return candidates


def init_all_candidates(w, h, hor, ver):
    ''' 得到所有行/列的所有排列 '''
    candi_h = [get_candidates(hor[i], w) for i in range(h)]
    candi_v = [get_candidates(ver[i], h) for i in range(w)]
    return candi_h, candi_v


def filtrate(candidates, pos, symbol):
    ''' 筛选出某一行/列的符合规则的排列 '''
    if candidates == "done":
        return candidates
    return [line for line in candidates if line[pos] == symbol]


def solve(filename):
    size, hor, ver = get_data(filename)
    w, h = size[0]
    candi_h, candi_v = init_all_candidates(w, h, hor, ver)
    res = [['0']*w for _ in range(h)]
    cnt, target = 0, w*h
    while cnt < target:
        # 先针对每一行
        for row, lines in enumerate(candi_h):
            if lines == "done":
                continue
            elif len(lines) == 1:
                cnt += res[row].count('0')
                for col in range(w):
                    res[row][col] = lines[0][col]
                    candi_v[col] = filtrate(candi_v[col], row, lines[0][col])
                candi_h[row] = "done"
            else:
                for col in range(w):
                    if res[row][col] == '0':
                        for line in lines[1:]:
                            if line[col] != lines[0][col]:
                                break
                        else:
                            cnt += 1
                            res[row][col] = lines[0][col]
                            candi_v[col] = filtrate(candi_v[col], row, lines[0][col])
        # 再针对每一列
        for col, lines in enumerate(candi_v):
            if lines == "done":
                continue
            elif len(lines) == 1:
                for row in range(h):
                    if res[row][col] == '0':
                        cnt += 1
                        res[row][col] = lines[0][row]
                        candi_h[row] = filtrate(candi_h[row], col, lines[0][row])
                candi_v[col] = "done"
            else:
                for row in range(h):
                    if res[row][col] == '0':
                        for line in lines[1:]:
                            if line[row] != lines[0][row]:
                                break
                        else:
                            cnt += 1
                            res[row][col] = lines[0][row]
                            candi_h[row] = filtrate(candi_h[row], col, lines[0][row])
    return res


if __name__ == "__main__":
    res = solve("up.txt")
    new = [''.join(line)+'\n' for line in res]
    print(''.join(new))
```

\>>>

```txt
                   ### ##
                  ########
                 ##########
                 ###   #  #
                 ##### ## #
                 ##### ## #
                ####   #  #
             ###############
           ###################
          ###### ##############
         ######   # ############
         ######     # ##########
        #######   ##  # ########
        ###### # # ##   # # #  #
        #####   #  ####        #
        ##### #### # #### # # #
        #####   # #   ########
         ##### ##  #   ########
         ######  #  ##   # ###
          ###### ###  ##     #
           ######   #   #####
#           ######  ###
##           #######   ##
###  ###   ########## ####
######### ############    #
######################    #
 ##################### ####
  #  #################    #
   ##  ######## #####     #
        ##     ##     ####
          #####  ## #   #
                   #####
```

- 迷你龙？不，是一条 Python
- 登入 `http://www.pythonchallenge.com/pc/rock/python.html`，得到
- 图片

    ![Python](.\imgs\32_python.png)

- 提示

    > Congrats! You made it through to the smiling python.
    >
    > "Free" as in "Free speech", not as in "free...

- 搜索得知，这是开源社区流行的一句话：`“Free as in Speech” or “Free as in Beer”`

## 5. 答案

- `http://www.pythonchallenge.com/pc/rock/beer.html`