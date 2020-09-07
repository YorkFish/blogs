# 1. Package Control

!!! note
    - 官网地址：<a href="https://packagecontrol.io/" target="_blank">>>> 传送门</a>
    - 中文镜像：<a href="http://packagecontrol.cn/" target="_blank">>>> 传送门</a>

## 1. 安装

1. <kbd>Ctrl</kbd> + <kbd>\`</kbd> 或 `View` > `Show Console` : 打开控制台
2. 输入下方代码

    ```python
    import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.cn/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
    ```

3. 等待一段时间

## 2. 修改插件 channels

1. `Preferences` > `Settings`
2. 写入如下语句，保存、退出

    ```json
    "channels":
    [
        "http://packagecontrol.cn/channel_v3.json"
    ],
    ```

3. 重启软件即可

### 补充

- 可以把 `http://packagecontrol.cn/channel_v3.json` 的文本拷贝到本地
- 用本地路径代替网络路径，如下

    ```json
    "channels":
    [
        "E:/SublimeProjects/channel_v3.json"
    ],
    ```

## 3. 使用

1. 按 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> 打开命令面板
2. 输入 `Package Control: Install Package`，回车
3. 等左下角的 `Loading repositories[ =  ]` 跳完，会弹出新的面板
4. 输入 `Package` 的名称，按下回车即可自动安装相应的插件

## 4. 卸载

1. 按 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> 打开命令面板
2. 输入 `Package Control: Remove Package`，回车
3. 选择要卸载的插件，单击或回车都行
