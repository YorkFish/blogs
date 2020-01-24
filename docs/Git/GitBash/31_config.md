# *config*

- 从 `config` 命令开始，从 `config` 命令结束

## 1. 让命令更醒目的命令

> york$ git config --global color.ui true

## 2. 偷懒的命令

- 有点像在 *Vim* 里设置快捷键

> york$ git config --global alias.st status

- 命令含义：以后， `st` 与 `status` 一个意思

## 3. 常用的缩写[^1]

> - $ git config --global alias.co checkout
> - $ git config --global alias.ci commit
> - $ git config --global alias.br branch
> - $ git config --global alias.unstage 'reset HEAD'
>     - $ git unstage test.py
>     - $ git reset HEAD test.py
> - $ git config --global alias.last 'log -1'
>     - $ git last
>     - 显示最近一次的提交
> - $ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

***

[^1]: 摘取自廖雪峰老师的《Git教程》