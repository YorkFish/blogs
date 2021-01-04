# 9. 在本地建一个仓库

!!! note ""
    方便起见，我删除了之前的文件夹

## 1. 选路径

```bash
York@DESKTOP MINGW64 /d/git
$ mkdir git_note

York@DESKTOP MINGW64 /d/git
$ cd git_note

York@DESKTOP MINGW64 /d/git/git_note
$ 
```

## 2. 初始化

```bash
York@DESKTOP MINGW64 /d/git/git_note
$ git init
Initialized empty Git repository in D:/git/git_note/.git/
```

## 3. 查看

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ ls -a
./  ../  .git/
```

!!! note
    - `git_note` 下新增了一个名为 `.git` 的隐藏文件夹
    - 路径后多了一个 `(master)`
