# 第 *20* 题 *go away!*

## 1. 地址

- <a href="http://www.pythonchallenge.com/pc/hex/idiot2.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/idiot2.html</a>

## 2. 图片

![unreal](.\imgs\20_unreal.jpg)

## 3. 提示

- 网页内

    > but inspecting it carefully is allowed.

## 4. 解法

### part1

1. 题图名称：`unreal`
2. 按 <kbd>F12</kbd>，查看“请求头”

    ```
    Content-Range: bytes 0-30202/2123456789
    Content-Type: image/jpeg
    Date: Sat, 07 Mar 2020 06:43:14 GMT
    Server: lighttpd/1.4.35
    Transfer-Encoding: chunked
    ```

3. 对比上一题的“请求头”

    ```
    Accept-Ranges: bytes
    Content-Length: 45552
    Content-Type: image/jpeg
    Date: Sat, 07 Mar 2020 06:44:54 GMT
    ETag: "886623682"
    Last-Modified: Sat, 12 Mar 2016 19:38:45 GMT
    Server: lighttpd/1.4.35
    ```

### part2

1. 使用 `requests`

    ```python
    import requests

    # request
    url = "http://www.pythonchallenge.com/pc/hex/unreal.jpg"
    usr_and_pwd = ("butter", "fly")
    res = get(url, auth=usr_and_pwd)
    # response
    print("Response Status Code:", res.status_code)
    print("Response Headers:", res.headers)
    print("Size of Content:", len(res.content), "bytes")
    print("Content:", repr(res.content[:200]))

    >>>
    Response Status Code: 200
    Response Headers: {'Content-Type': 'image/jpeg', 'Content-Range': 'bytes 0-30202/2123456789', 'Transfer-Encoding': 'chunked', 'Date': 'Sat, 07 Mar 2020 06:52:45 GMT', 'Server': 'lighttpd/1.4.35'}
    Size of Content: 30203 bytes
    Content: b'\xff\xd8\xff\xe0\x00\x10JFIF\x00\x01\x01\x01\x00H\x00H\x00\x00\xff\...'
    ```

2. 既然是 `unreal`，不妨从 `30202 + 1` 开始获取数据

    ```python
    from requests import get
    
    
    def get_unreal(start, stop=''):
        # request
        url = "http://www.pythonchallenge.com/pc/hex/unreal.jpg"
        usr_and_pwd = ("butter", "fly")
        res_range = {"Range": f"bytes={start}-{stop}"}
        res = get(url, auth=usr_and_pwd, headers=res_range)
        # response
        print("Response Status Code:", res.status_code)
        print("Content Range:", res.headers["Content-Range"])
        print("Size of Content:", len(res.content), "bytes")
        print("Content:", repr(res.content[:200]))
    
    
    if __name__ == "__main__":
        get_unreal(30203)
    
    >>>
    Response Status Code: 206
    Content Range: bytes 30203-30236/2123456789
    Size of Content: 34 bytes
    Content: b"Why don't you respect my privacy?\n"
    ```

3. 内容分析
    - `206` 表示“部分内容”
    - `30236` 之后还有

### part3

- 重复 part2 的第二步操作
1. 从 `30236 + 1` 开始，得到

    ```txt
    Response Status Code: 206
    Content Range: bytes 30237-30283/2123456789
    Size of Content: 47 bytes
    Content: b'we can go on in this way for really long time.\n'
    ```

2. 从 `30283 + 1` 开始，得到

    ```txt
    Response Status Code: 206
    Content Range: bytes 30284-30294/2123456789
    Size of Content: 11 bytes
    Content: b'stop this!\n'
    ```

3. 从 `30294 + 1` 开始，得到

    ```txt
    Response Status Code: 206
    Content Range: bytes 30295-30312/2123456789
    Size of Content: 18 bytes
    Content: b'invader! invader!\n'
    ```

4. 从 `30312 + 1` 开始，得到

    ```txt
    Response Status Code: 206
    Content Range: bytes 30313-30346/2123456789
    Size of Content: 34 bytes
    Content: b'ok, invader. you are inside now. \n'
    ```

5. 再重复，就没下文了
   
    - 抛出异常：`KeyError: 'content-range'`

### part4

1. `Content` 中出现了三次 `invader`，拿它试试

2. 打开 `http://www.pythonchallenge.com/pc/hex/invader.html`，得到

    > Yes! that's you!

### part5

- 电影《头号玩家》中，第一关的“赛车”是从后方倒车打通的，试试主角的方法

1. 从 `2123456789 - 1` 开始，得到

    ```txt
    Response Status Code: 206
    Content Range: bytes 2123456744-2123456788/2123456789
    Size of Content: 45 bytes
    Content: b'esrever ni emankcin wen ruoy si drowssap eht\n'
    ```

2. 分析结果
    - `Content` 的内容看着既像英文，又不像英文
    - 末尾的 `eht` 比较好认，反过来是 `the`
    - 同样的，把第一个词 `esrever` 反过来，结果是 `reverse`，这就明确了

3. reverse "Context"

    ```python
    >>> s = "esrever ni emankcin wen ruoy si drowssap eht"
    >>> s[::-1]
    'the password is your new nickname in reverse'
    >>> pwd = "invader"
    >>> pwd[::-1]
    redavni
    >>> 
    ```

### part6

- 重复 part5 的第一步操作

1. 从 `2123456744 - 1` 开始，得到

    ```txt
    Response Status Code: 206
    Content Range: bytes 2123456712-2123456743/2123456789
    Size of Content: 32 bytes
    Content: b'and it is hiding at 1152983631.\n'
    ```

2. 从 `1152983631` 开始，得到

    ```txt
    Response Status Code: 206
    Content Range: bytes 1152983631-1153223363/2123456789
    Size of Content: 239733 bytes
    Content: b'PK\x03\x04\x14\x00\t\x00\x08\x00;\xa7\xaa2\xac\xe5f\x14\xa9\x00\x00\x00\xd3\x00\x00\x00\n\x00\x15\x00readme.txtUT\t\x00\x03"\xf6\x80B\x19\xf7\x80BUx...'
    ```

3. 内容分析
    
    - `Content` 开头有个 `PK`，往后读还能看到 `readme.txt`
    
    - 搜索得知 `PK` 是 `.zip` 的文件头
4. 至此，反向走也到头了

### part7

1. 将 `res.content` 写入文件

    ```python
    from requests import get
    
    
    def get_unreal(start, stop=''):
        # request
        url = "http://www.pythonchallenge.com/pc/hex/unreal.jpg"
        usr_and_pwd = ("butter", "fly")
        res_range = {"Range": f"bytes={start}-{stop}"}
        res = get(url, auth=usr_and_pwd, headers=res_range)
        # response
        print("Response Status Code:", res.status_code)
        print("Content Range:", res.headers["Content-Range"])
        print("Size of Content:", len(res.content), "bytes")
    
        return res.content
    
    
    if __name__ == "__main__":
        f = open("unreal.zip", "wb")
        f.write(get_unreal(1152983631))
        f.close()
    ```

2. 打开 `unreal.zip`，内有两个文件，需要密码

3. 使用 part5 得到的密码 `redavni` 打开 `readme.txt`

    ```txt
    Yes! This is really level 21 in here. 
    And yes, After you solve it, you'll be in level 22!
    
    Now for the level:
    
    * We used to play this game when we were kids
    * When I had no idea what to do, I looked backwards.
    ```

4. 所以下一题是打开这个压缩包

## 5. 答案

- 压缩包密码：`redavni`