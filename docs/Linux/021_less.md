# *less*

## 1. 命令简介

- <u>文件处理命令</u>
- 命令所在路径：`/usr/bin/less`
- 执行权限：所有用户
- 功能描述：***分页显示文件内容***（可向上翻页）

## 2.命令语法

- `york$ less [文件名]`

### 常用按键

| 按键 | 效果 |
| :--: | :--- |
| <kbd>f</kbd> | 向下翻一页（将屏幕上移一页）；*forward*；<kbd>space</kbd>, <kbd>PgDn</kbd>, <kbd>z</kbd> 与其同效 |
| <kbd>b</kbd> | 向上翻一页（将屏幕下移一页）；*before*；<kbd>PgUp</kbd> 与其同效 |
| <kbd>d</kbd> | 向下翻半页（将屏幕上移半页）；*down* |
| <kbd>u</kbd> | 向上翻半页（将屏幕下移半页）；*up* |
| <kbd>e</kbd> | 向下翻一行（将屏幕上移一行）；<kbd>Enter</kbd> 与其同效 |
| <kbd>y</kbd> | 向上翻一行（将屏幕下移一行） |
| <kbd>q</kbd> | 退出（不区分大小写） |

- ps
    - 向下翻页的实质是屏幕向上移动
    - 在使用 *less* 命令时，按 <kbd>h</kbd> 可以查看帮助信息，获取更多的快捷键

## 3. 举例

- `york$ less /etc/services`