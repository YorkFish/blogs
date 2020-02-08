# *ifconfig*

## 1. 命令简介

- <u>网络命令</u>
- 命令名称：<font color=#0099ff size=5>i</font>nter<font color=#0099ff size=5>f</font>ace <font color=#0099ff size=5>config</font>ure
- 命令所在路径：`/sbin/ifconfig`
- 执行权限：*root*
- 功能描述：***查看和设置网卡信息***

## 2. 命令语法

- `york$ ifconfit 网卡名称 IP地址`

## 3. 举例

- `york$ ifconfig eth0 192.168.8.250`

    | 数据 | 释义 |
    | :---: | :--- |
    | **eht0** | 本地网卡，往后是 *eth1, eht2* ... |
    | **l0** | 回环网卡、本机测试和通讯 |
    | **Bcast** | 当前网络地址 |
    | **Mask** | 磁盘原码 |
    | **RX** | 接收 |
    | **TX** | 发送 |
