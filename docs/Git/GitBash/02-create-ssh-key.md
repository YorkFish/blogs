# 2. 创建 SSH Key

## 1. 输入命令

- 命令格式：`ssh-keygen -t rsa -C "abc@email.com"`，如

    ```bash
    York@DESKTOP MINGW64 ~/Desktop
    $ ssh-keygen -t rsa -C "york@email.com"
    ```

- 命令反馈
    1. `Enter passphrase (empty for no pass phrase):`
    2. `Enter same passphrase again:`
- 若没有特别要求，直接回车即可
- 回车后会打印出一张 `randomart image`，类似下图

    ```
    +---[RSA 2048]----+
    |       o . . o . |
    |     * =     B * |
    |       o . . * . |
    |         . B   o |
    |     .     .   + |
    | o o   * . o . B |
    |  = o   *        |
    +----[SHA256]-----+
    ```

## 2. 复制公钥

- 此时 `C:\Users\xxx\` 下会有一个隐藏文件夹：`.ssh`，里面有三个文件
    1. `id_rsa`
    2. `id_rsa.pub`
    3. `known_hosts`
- 说明
    - `id_rsa` 是私钥，不要泄露了
    - `id_rsa.pub` 是公钥，可以让他人知道
- 操作
    1. 打开 `id_rsa.pub`
    2. 复制里面的一堆文本
