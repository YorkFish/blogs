# 第 *01* 题 *What about making trans?*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/def/map.html" target="target">>>> http://www.pythonchallenge.com/pc/def/map.html</a>

## 2. 题图

![map](.\imgs\01_map.jpg)

## 3. 提示

> everybody thinks twice before solving this.

```txt
g fmnc wms bgblr rpylqjyrc gr zw fylb. rfyrq ufyr amknsrcpq ypc dmp. bmgle gr gl zw fylb gq glcddgagclr ylb rfyr'q ufw rfgq rcvr gq qm jmle. sqgle qrpgle.kyicrpylq() gq pcamkkclbcb. lmu ynnjw ml rfc spj.
```

## 4. 解法

1. 图中示意将字母往后移两位

    ```txt
    ... K, L, M ...
    ... O, P, Q ...
    ... E, F, G ...
    ```

2. 非字母部分没说，就不做理会

    ```python
    s = "g fmnc wms bgblr rpylqjyrc gr zw fylb. rfyrq ufyr amknsrcpq ypc dmp. bmgle gr gl zw fylb gq glcddgagclr ylb rfyr'q ufw rfgq rcvr gq qm jmle. sqgle qrpgle.kyicrpylq() gq pcamkkclbcb. lmu ynnjw ml rfc spj."
    
    res = [e.isalpha() and chr(97 + (ord(e)-97+2) % 26) or e for e in s]
    print(''.join(res))
    
    >>> 
    i hope you didnt translate it by hand. thats what computers are for. doing it in by hand is inefficient and that's why this text is so long. using string.maketrans() is recommended. now apply on the url.
    ```

3. 上面的结果提示：使用 `string.maketrans()` 对地址进行“翻译”
4. 不过 *Python3.4* 起，`maketrans()` 成为了内建函数

    ```python
    s = "map"
    intab = ''.join([chr(e) for e in range(97, 123)])
    outtab = ''.join([chr(97 + (e-97+2) % 26) for e in range(97, 123)])
    transtab = str.maketrans(intab, outtab)
    print(s.translate(transtab))
    
    >>> 
    ocr
    ```

## 5. 答案

- `http://www.pythonchallenge.com/pc/def/ocr.html`