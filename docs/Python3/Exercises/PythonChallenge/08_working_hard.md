# 第 *8* 题 *working hard?*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/def/integrity.html" target="_blank">>>> http://www.pythonchallenge.com/pc/def/integrity.html</a>

## 2. 题图

![integrity](.\imgs\08_integrity.jpg)

## 3. 提示

- 网页内

    > Where is the missing link?

- 网页源码注释

    ```txt
    un: 'BZh91AY&SYA\xaf\x82\r\x00\x00\x01\x01\x80\x02\xc0\x02\x00 \x00!\x9ah3M\x07<]\xc9\x14\xe1BA\x06\xbe\x084'
    pw: 'BZh91AY&SY\x94$|\x0e\x00\x00\x00\x81\x00\x03$ \x00!\x9ah3M\x13<]\xc9\x14\xe1BBP\x91\xf08'
    ```

## 4. 解法

### part1

- 点击图中蜜蜂，页面会跳转到一个登录界面
- 可以猜测：源码中的 `un` 与 `pw` 对应这里的 `username` 与 `password`

### part2

- 蜜蜂的英文 *Bee* 与 *BZ2* 形似
- `BZh91...` 正是使用 `bz2` 压缩后的文件头

    ```python
    from bz2 import decompress
    
    un = b"BZh91AY&SYA\xaf\x82\r\x00\x00\x01\x01\x80\x02\xc0\x02\x00 \x00!\x9ah3M\x07<]\xc9\x14\xe1BA\x06\xbe\x084"
    pw = b"BZh91AY&SY\x94$|\x0e\x00\x00\x00\x81\x00\x03$ \x00!\x9ah3M\x13<]\xc9\x14\xe1BBP\x91\xf08"
    print("un:", decompress(un))
    print("pw:", decompress(pw))
    
    >>>
    un: b'huge'
    pw: b'file'
    ```

## 5. 答案

- 新页面：`http://www.pythonchallenge.com/pc/return/good.html`
    - 账号：`huge`
    - 密码：`file`
- ps
    - 接下来的几题，若关闭浏览器后重新打开，每次均需输入上述的账号、密码