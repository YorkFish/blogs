# 6. 本地仓库向远程仓库推送

## 1. 推送

- 第一次推送时需要加 `-u`
- 第二次及以后，再推送这个仓库中的内容时，就不需要加 `-u` 了

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git push -u origin master
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 4 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (11/11), 1.02KiB | 69.00 KiB/s, done.
Total 11 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To github.com:YorkFish/git_note_online.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

!!! quote
    - 由于远程库是空的，我们第一次推送 `master` 分支时，加上了 `-u` 参数，
    - Git 不但会把本地的 `master` 分支内容推送的远程新的 `master` 分支，
    - 还会把本地的 `master` 分支和远程的 `master` 分支关联起来，
    - 在以后的推送或者拉取时就可以简化命令。[^1]

## 2. 查看

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git log --oneline
3f06ce7 (HEAD -> master, origin/master) add will_be_deleted.txt
67dc44a add sentence 3 add sentence 4
9884432 add note_01.txt
6cc65c6 add README.md
```

!!! note
    - 最新版本号后面多了 `origin/master`
    - 这表明：远程仓库的 `master` 分支正指向版本 `3f06ce7`

***

## 补充

### 1. GitHub 上的地址

- 有两种地址，即，有两种加密传输方式
    1. `https`
    2. `SSH`

### 2. 没有设置 origin 也能工作

- 方法：用具体的地址，如
    - `git push git@github.com:YorkFish/git_note_online.git master`

### 3. 可以删除 origin

- `git remote rm origin`

### 4. 可以设置多个 origin

- 可以这样取名：`origin1`, `origin2`, ...

[^1]: 摘自廖雪峰老师的Git教程
