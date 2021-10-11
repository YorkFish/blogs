## 1. 设定用户配置目录

- `path\to\Rime\MyConfigData`

## 2. 添加英文库

- 说明：需要有相应的文件
- 步骤
    1. 把文件 `easy_en_dict.yaml`, `easy_en_schema.yaml` 拷贝到 `MyConfigData`
    2. 右键右下角输入法图标 -> 输入法设定 -> 勾选 `Easy English` -> 中
    3. 等待“维护”即可

## 3. 添加小鹤双拼

- 文件地址：`https://github.com/rime/rime-double-pinyin`

### 方式一

1. 解压
2. 将 `double_pinyin_flypy.schema.yaml` 拷贝到 `MyConfigData`
3. 右键右下角输入法图标 -> 输入法设定 -> 勾选 `小鶴雙拼` -> 中
4. 等待“维护”即可

### 方式二

1. 右键右下角输入法图标 -> 输入法设定
2. 点击弹窗左下角的“获取更多输入方案”（需要登录 GitHub）
3. 在弹窗的 `Enter package name, URL, user/repo or downloaded ZIP to install:` 后输入相应信息，等待安装
4. 勾选 `小鶴雙拼` -> 中
5. 等待“维护”

## 4. 添加五笔

- 文件地址：`https://github.com/rime/rime-wubi`
- 方法与“小鹤双拼”一样
- 目前是纯五笔

### 五笔-拼音

- 再装一个“袖珍简化字拼音”即可
- 文件地址：`https://github.com/rime/rime-pinyin-simp`
- 将 `pinyin_simp.dict.yaml`, `pinyin_simp.schema.yaml` 拷贝到 `MyConfigData`
- 重新部署一下

## 5. 更改功能键

### 步骤

1. 打开 `path\to\Rime\MyConfigData\default.custom.yaml`
2. 在 `patch:` 下添加语句

   ```yaml
    "menu/page_size": 7
    "ascii_composer/switch_key":
      Caps_Lock: noop
      Shift_L: commit_code
      Shift_R: commit_code
   ```

3. 重新部署

### 解释

| 模式 | 释义 |
| :--- | :--- |
| inline_ascii | 中文状态下输入字母、数字、符号、空格等，回车上屏 |
| commit_text  | 中文状态下，已输入的候选文字以中文形式上屏，然后切至英文 |
| commit_code  | 中文状态下，已输入的候选文字以英文形式上屏，然后切至英文 |
| noop         | 屏蔽该切换键 |


## 6. 取消一键多值

### 说明

- 方法不唯一

### 我选的方式

1. 将 `path\to\Rime\weasel-0.14.3\data\symbols.yaml` 复制到 `path\to\Rime\MyConfigData` 并重命名为 `symbols.custom.yaml`
2. 打开并找到 `half_shape`，删除不想要的多值，如下方这样

    ```yaml
    half_shape:
        "!": {commit: "！"}
        "\"": {pair: ["“", "”"]}
        "#": "#"
        "$": "￥"
        "%": "%"
        "&": "&"
        "'": {pair: ["‘", "’"]}
        "(": "（"
        ")": "）"
        "*": "*"
        "+": "+"
        ",": {commit: "，"}
        "-": "-"
        .: {commit: "。"}
        "/": ["、", "/"]  # 这句是为特殊符号的妥协
        ":": {commit: "："}
        ";": {commit: "；"}
        "<": "《"
        "=": "="
        ">": "》"
        "?": {commit: "？"}
        "@": "@"
        "[": "["
        "\\": "、"
        "]": "]"
        "^": {commit: "……"}
        _: "——"
        "`": "`"
        "{": "{"
        "|": "|"
        "}": "}"
        "~": "~"
    ```

3. 在 `MyConfigData` 下新建文件 `double_pinyin_flypy.custom.yaml`
    - 别的输入法类似，如 `wubi_pinyin.custom.yaml`
4. 写入如下语句

    ```yaml
    patch:
      'punctuator/import_preset': symbols.custom
    ```

5. 重新部署

### 其他方式对应的配置文件

- `path\to\Rime\MyConfigData\build\default.yaml`
- `path\to\Rime\MyConfigData\build\double_pinyin_flypy.schema.yaml`
- `path\to\Rime\MyConfigData\default.custom.yaml`
- `path\to\Rime\MyConfigData\weasel.custom.yaml`

## 7. 添加特殊符号快捷键

### 说明

- 以下是单个输入法的配置
- 用的是补丁 `*.custom.yaml` 的语法，不适用于源文件

### 步骤

1. 打开相应输入法的补丁配置文件，如 `double_pinyin_flypy.custom.yaml`
2. 在 `patch:` 下添加语句

    ```yaml
    'recognizer/patterns/punct': '^/([0-9]0?|[A-Za-z]+)$'
    ```

3. 重新部署
