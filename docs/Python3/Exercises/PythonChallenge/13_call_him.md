# 第 *13* 题 *call him*

## 1. 地址

<a href="http://www.pythonchallenge.com/pc/return/disproportional.html" target="_blank">>>> http://www.pythonchallenge.com/pc/return/disproportional.html</a>

## 2. 题图

![disprop](.\imgs\13_disprop.jpg)

## 3. 提示

> phone that evil

## 4. 解法

### part1

1. `evil` 在“九键”中的对应的数字依次为 <kbd>3</kbd> <kbd>8</kbd> <kbd>4</kbd> <kbd>5</kbd>
2. 当鼠标移入 <kbd>5</kbd> 的范围时，发现 `Button`
3. 点击后，网页跳转，得到如下

    ```xml
    <methodResponse>
      <fault>
        <value>
          <struct>
            <member>
              <name>faultCode</name>
            <value>
              <int>105</int>
            </value>
            </member>
            <member>
              <name>faultString</name>
            <value>
              <string>
                XML error: Invalid document end at line 1, column 1
              </string>
            </value>
            </member>
          </struct>
        </value>
      </fault>
    </methodResponse>
    ```

### part2

1. 上方的信息是暗示使用 *Python* 处理 *XML*
2. 搜索得知 `xmlrpc` 库

    ```python
    >>> from xmlrpc import client
    >>> conn = client.ServerProxy("http://www.pythonchallenge.com/pc/phonebook.php")
    >>> conn
    <ServerProxy for www.pythonchallenge.com/pc/phonebook.php>
    >>> conn.system.listMethods()
    ['phone', 'system.listMethods', 'system.methodHelp', 'system.methodSignature', 'system.multicall', 'system.getCapabilities']
    >>> 
    >>> 
    >>> conn.system.methodHelp("phone")
    'Returns the phone of a person'
    >>> conn.system.methodSignature("phone")
    [['string', 'string']]
    >>> 
    >>> 	
    >>> conn.phone("Bert")  # 上一题说 Bert is evil
    '555-ITALY'
    ```

3. 在美国，以 `555` 打头的是空号，所以此题的解为 `italy`

## 5. 答案

- `http://www.pythonchallenge.com/pc/return/italy.html`