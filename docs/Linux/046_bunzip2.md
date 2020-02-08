# *bunzip2*

## 1. 命令简介

- <u>压缩解压命令</u>
- 命令所在路径：`/usr/bin/bunzip2`
- 执行权限：所有用户
- 功能描述：***解压缩***

## 2. 命令语法

- `bunzip2 选项[-k] [压缩文件]`
    - `-k`：解压缩后保留原文件

## 3. 举例

1. 给压缩包 *boduo.bz2* 解压
    - `york$ bunzip2 -k buoduo.bz2`
2. 使用 *tar* 命令给压缩包 *Japan.tar.bz2* 解压
    - `york$ tar -xjf Japan.tar.bz2`