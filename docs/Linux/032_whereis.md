# *whereis*

## 1. 命令简介

- <u>文件搜索命令</u>
- 命令所在路径：`/bin/whereis`
- 执行权限：所有用户
- 功能描述：***搜索命令所在目录及帮助文档路径***

## 2. 命令语法

- `york$ whereis [命令名称]`

## 3. 举例

- `york$ whereis ls`

### 补充

    york$ whereis useradd
    useradd: /usr/sbin/useradd /usr/share/man/man8/useradd.8.gz

- `/usr/sbin/useradd` 表示绝对路径
- `/usr/share/man/man8/useradd.8.gz` 表示命令帮助文档

- 大多数帮助文档存在于 `/usr/share` 中
- *man* 指的是“首选项” *manue*