# 1. 设置身份信息

## 1. 说明

- 因为本地仓库和 GitHub 上的远程仓库之间的传输是通过 `SSH/HTTPS` 加密的，所以使用前需要做一些设置
- 这一步可在刚安装完 Git 时做，也可以之后再做
- 建议以“管理员身份”打开 Git Bash

## 2. user\.name

- 命令格式：`git config --global user.name "name"`，如

    ```bash
    York@DESKTOP MINGW64 ~/Desktop
    $ git config --global user.name "York"
    ```

- 命令反馈：无

## 3. user\.email

- 命令格式：`git config --global user.email "abc@email.com"`
- 命令说明：邮箱可以用真实的，也可以用不存在的，如

    ```bash
    York@DESKTOP MINGW64 ~/Desktop
    $ git config --global user.email "york@email.com"
    ```

- 命令反馈：无

## 4. 查看信息

```bash
York@DESKTOP MINGW64 ~/Desktop
$ git config user.name
York

York@DESKTOP MINGW64 ~/Desktop
$ git config user.email
york@email.com
```
