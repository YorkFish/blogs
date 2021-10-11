# Convert​To​UTF8

!!! note
    - 官方文档：<a href="http://packagecontrol.cn/packages/ConvertToUTF8" target="_blank">>>> 传送门</a>
    - 这个貌似逃不掉，早晚得装

## 1. 说明

我装的时候无法访问官网，所以我是从 GitHub 上的<a href="https://github.com/seanliang/ConvertToUTF8" target="_blank">仓库</a>下载的

## 2. 安装

1. 下载 zip 文件
2. 解压
3. 将文件重命名为 `ConvertToUTF8`
4. 点击 `Preferences` > `Browse Packages`
5. 将文件 `ConvertToUTF8` 剪切至 `Browse Packages`
6. 重启一下

## 3. 补充

- 官方推荐的配置
- 点击 `Preferences` > `Packages Settings` > `ConvertToUTF8` > `Settings - User`

```json
{
    // supported encoding list, name & code in pair
    "encoding_list" : [
        ["Chinese Simplified (GBK)", "GBK"],
        ["Chinese Simplified (GB2312)", "GB2312"],
        ["Chinese Simplified (GB18030)", "GB18030"],
        ["Chinese Traditional (BIG5)", "BIG5"],
        ["Korean (EUC-KR)", "EUC-KR"],
        ["Japanese (CP932)", "CP932"],
        ["Japanese (Shift_JIS)", "Shift_JIS"],
        ["Japanese (EUC-JP)", "EUC-JP"],
        ["UTF-8", "UTF-8"]
    ],

    // Reset diff markers after converting
    "reset_diff_markers" : true,

    // Maximum size for encoding cache, 0 means no cache
    "max_cache_size" : 100,

    // Maximum lines to detect, 0 means unlimited
    "max_detect_lines" : 600,

    // Convert when previewing file: true or false
    "preview_action" : false,

    // Encoding for new file, empty means using sublime text's "default_encoding" setting
    "default_encoding_on_create" : "",

    // Set this option to true will cause Sublime Text reload the saved file when losing focus
    "lazy_reload": false,

    // The minimum confidence rate between 0.0 and 1.0
    "confidence": 0.95,

    // Convert in Find Results view
    "convert_on_find": false,

    // Convert when loading/saving a file
    "convert_on_load" : true,
    "convert_on_save" : true
}
```
