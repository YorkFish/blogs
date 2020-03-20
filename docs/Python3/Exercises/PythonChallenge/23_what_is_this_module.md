# 第 *23* 题 *what is this module?*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/hex/bonus.html" target="_blank">>>> http://www.pythonchallenge.com/pc/hex/bonus.html</a>

## 2. 题图

![bonus](.\imgs\23_bonus.jpg)

## 3. 提示

- 网页源码注释
  
    > TODO: do you owe someone an apology? now it is a good time to tell him that you are sorry. Please show good manners although it has nothing to do with this level.
    >
    > 
    >
    > it can't find it. this is an undocumented module.
    >
    > 
    >
    > va gur snpr bs jung?'

## 4. 解法

### part1

1. 说到 `apology`，第 *19* 题令人印象深刻
    - 解题过程中生成了一个 `indian.wav`，有一声 `sorry`
    - 进入新页面时，`Leopold` 的肖像下方有一句 `"Now you should apologize..."`
    - 那一题有 `Leopold` 的邮箱地址：`leopold.moz@pythonchallenge.com`
2. 发一封道歉信吧，虽然上面说 `it has nothing to do with this level`，显然这是后面的题目的线索
3. 很快就得到了 `Leopold` 的回复

    > Never mind that.
    >
    > Have you found my broken zip?
    >
    > md5: bbb8b499a0eef99b52c7f13f4e78c24b
    >
    > Can you believe what one mistake can lead to?

### part2

1. `this is an undocumented module`
    - `this` 是双关语，除了原来的意思，还代表 `this` 模块
    - 这个模块正好没有说明文档
2. 搜索得知这个网页：`https://legacy.python.org/dev/peps/pep-0020/`
3. 该网页题为：`PEP 20 -- The Zen of Python`，即“Python 之禅”
4. 拉倒网页下方，可以看见“复活节彩蛋”

    > Easter Egg
    >
    > \>>> import this

5. 导入模块，会立即输出“Python 之禅”

    ```python
    >>> import this
    The Zen of Python, by Tim Peters
    
    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!
    >>> 
    ```

### part3

1. 这里有 *Python2* 的`this` 源码：`https://svn.python.org/projects/python/trunk/Lib/this.py`
2. 在安装目录也能找到，比如我的是在 `E:\Anaconda3\Lib\this.py`

    ```python
    s = """Gur Mra bs Clguba, ol Gvz Crgref
    
    Ornhgvshy vf orggre guna htyl.
    Rkcyvpvg vf orggre guna vzcyvpvg.
    Fvzcyr vf orggre guna pbzcyrk.
    Pbzcyrk vf orggre guna pbzcyvpngrq.
    Syng vf orggre guna arfgrq.
    Fcnefr vf orggre guna qrafr.
    Ernqnovyvgl pbhagf.
    Fcrpvny pnfrf nera'g fcrpvny rabhtu gb oernx gur ehyrf.
    Nygubhtu cenpgvpnyvgl orngf chevgl.
    Reebef fubhyq arire cnff fvyragyl.
    Hayrff rkcyvpvgyl fvyraprq.
    Va gur snpr bs nzovthvgl, ershfr gur grzcgngvba gb thrff.
    Gurer fubhyq or bar-- naq cersrenoyl bayl bar --boivbhf jnl gb qb vg.
    Nygubhtu gung jnl znl abg or boivbhf ng svefg hayrff lbh'er Qhgpu.
    Abj vf orggre guna arire.
    Nygubhtu arire vf bsgra orggre guna *evtug* abj.
    Vs gur vzcyrzragngvba vf uneq gb rkcynva, vg'f n onq vqrn.
    Vs gur vzcyrzragngvba vf rnfl gb rkcynva, vg znl or n tbbq vqrn.
    Anzrfcnprf ner bar ubaxvat terng vqrn -- yrg'f qb zber bs gubfr!"""
    
    d = {}
    for c in (65, 97):
        for i in range(26):
            d[chr(i+c)] = chr((i+13) % 26 + c)
    
    print("".join([d.get(c, c) for c in s]))
    ```

3. 借用 `this.py` 的字典

    ```python
    >>> import this
    ...  # 省略若干
    >>> s = "va gur snpr bs jung?"
    >>> ''.join([this.d.get(c, c) for c in s])
    'in the face of what?'
    >>> 
    ```

4. 查看原文后得知：`In the face of ambiguity`

## 5. 答案

- `http://www.pythonchallenge.com/pc/hex/ambiguity.html`