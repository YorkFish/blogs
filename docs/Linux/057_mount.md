# *mount*

## 1. 命令简介

- <u>挂载命令</u>
- 命令所在路径：`/bin/mount`
- 执行权限：***所有用户***

## 2. 命令语法

- `york$ mount [-t 文件系统] 设备文件名 挂载点`

## 3. 举例

1. 挂载光盘
    - `york$ mount -t iso9660 /dev/sro /mnt/cdrom`
2. 缷载光盘
    - `york$ umount /dev/sro`