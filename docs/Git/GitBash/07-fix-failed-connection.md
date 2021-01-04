# 7. 解决连结失败的问题

!!! failure "抛出的问题"
    ssh: connect to host github.com port 22: Connection timed out

## 1. 检查

1. 进入相应目录
2. 右键，选择 `Git Bash Here`
3. 执行 `ssh -T git@github.com` 命令，若显示如下，则说明出了问题

    ```bash
    York@DESKTOP MINGW64 /d/hello-world (master)
    $ ssh -T github.com
    ssh: connect to host github.com port 22: Connection timed out
    ```

## 2. 解决方法

!!! note ""
    有两种常见的解决方法

### 方法一 使用 https 传输

- 删除原先的 `origin`，添加新的 `origin`
    1. `git remote rm origin`
    2. `git remote add origin https://github.com/YorkFish/xxx.git`

### 方法二 两步走

#### 第一步 重建秘钥

1. 使用命令 `ssh-keygen -t rsa -C "abc@email.com"` 重建秘钥
2. 登入 `GitHub`
3. 删除原先的公钥

    ![](.\imgs\07-01_delete_ssh_key.png)

4. 确认（此时可能需要输入登录密码以确认身份）

    ![](.\imgs\07-02_cconfirm_delete.png)

5. 添加新的 SSH Key
6. 使用 `ssh -T git@github.com` 检查，若仍不行，再走第二步（大概率是要走的）

#### 第二步 添加 config

- 在存放公钥 `id_rsa.pub` 的文件夹 `C:\Users\{username}\.ssh` 里，新建文本 `config`
- 在 `config` 中写入如下内容

    ```
    Host github.com
    User YourEmail@163.com
    Hostname ssh.github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa
    Port 443
    ```

!!! info
    第二行的 `User` 为你的 Github 账号名，后面跟设置的邮箱

### 检验

1. 执行 `ssh -T git@github.com`
2. 出现如下方第 5 行的提示，填 `yes`，然后回车即可

    ```bash
    York@DESKTOP MINGW64 ~/Desktop
    $ ssh -T github.com
    The autheticity of host '[ssh.github.com]:443 ([192.30.253.123]:443)' can't be established.
    RSA key fingerprint is SHA256:nThbg6kXUpJWG17E1IGOCspRomTxdCARLviKw6E5SY8.
    Are you sure want to continue connecting (yes/no)? yes
    Warning: Permanently added '[ssh.github.com]:443,[192.30.253.123]:443' (RSA) to the list of known hosts.
    Hi YorkFish! You've successfully authenticated, but GitHub does not provide shell access.
    ```

3. 这时，验证就可以通过了
4. 若再次执行 `ssh -T git@github.com`，显示如下

    ```bash
    York@DESKTOP MINGW64 /d/hello-world (master)
    $ ssh -T github.com
    Hi YorkFish! You've successfully authenticated, but GitHub does not provide shell access.
    ```
