# *grep*

## 1. 命令简介

- <u>文件搜索命令</u>
- 命令所在路径：`/bin/grep`
- 执行权限：所有用户
- 功能描述：***在文件中搜索字串匹配的行并输出***

## 2. 命令语法

- `grep -iv [指定字串] [文件]`
    - `-i` 表示不区分大小写
    - `-v` 表示排除指定字串

## 3. 举例

- `york$ grep mysql /root/install.log`

### 补充

1. 去掉有 `#` 的行
    - `york$ grep -v # /etc/inittab`
2. 去掉以 `#` 开头的行
    - `york$ grep -v ^# /etc/inittab`
3. 搭配“正则” ...