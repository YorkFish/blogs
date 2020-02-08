# *umask*

## 1. 命令简介

- <u>权限管理命令</u>
- 命令英文原意：the <font color=#0099ff size=5>u</font>ser file-creation <font color=#0099ff size=5>mask</font>
- 命令所在路径：*Sell* 内置命令
- 执行权限：所有用户
- 功能描述：***显示、设置文件的缺省权限***

## 2. 命令语法

- `umask [-S]`
    - `-S` 以 *r, w, x* 形式显示新建文件缺省权限

## 3. 举例

### 3.1 例1

1. 命令：`umask -S` & `umask`
2. 操作

    ![](.\imgs\28-01_umask1.png)

3. 分析
    - 上图 *umask* 返回的 *0002* 中
    - 第**一**个数字 *0*：表示特殊权限
    - 第**二**个数字 *0*：对应 *user*
    - 第**三**个数字 *0*：对应 *group*
    - 第**四**个数字 *2*：对应 *others*

### 3.2 例2

1. 目标：将权限改为 `rwxr-xr--` （即 *777-023*）
2. 命令：`umask 023`
3. 操作

    ![](.\imgs\28-02_umask2.png)