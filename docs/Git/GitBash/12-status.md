# 12. status

## 1. 加参数 \-s

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git status -s

York@DESKTOP MINGW64 /d/git/git_note (master)
$ git status
On branch master
nothing to commit, working tree clean
```

!!! note "说明"
    `git status -s` 显示的信息比 `git status` 简洁

## 2. 更多表现

### 2.1 添加文件

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ touch note_01.txt

York@DESKTOP MINGW64 /d/git/git_note (master)
$ ls
note_01.txt  README.md
```

### 2.2 写入文字

- 往 `note_01.txt` 中写入

```
1. git init 初始化

2. git status 查看

```

### 2.3 查看状态

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git status -s
?? note_01.txt
```

!!! note "说明"
    末行开头红色的 <font color="red">??</font> 依次说明 `note_01.txt` 还没有进行过 `add` 与 `commit`

### 2.4 添加 + 查看

- 将 `note_01.txt` 加入暂存区并查看状态

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git add note_01.txt

York@DESKTOP MINGW64 /d/git/git_note (master)
$ git status -s
A  note_01.txt
```

!!! note "说明"
    - 末行开头绿色的 <font color="green">A</font> 说明 `note_01.txt` 已经被加到暂存区了

### 2.5 继续写入

- 继续往 `note_01.txt` 中写入文字

```
1. git init 初始化

2. git status 查看

3. git add <file> 将 <file> 加入暂存区

```

### 2.6 查看状态

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git status -s
AM note_01.txt
```

!!! note "说明"
    - 末行开头
    - 绿色的 <font color="green">A</font> 说明暂存区已经有一个版本的 `note_01.txt`
    - 红色的 <font color="red">M</font> 说明工作区的 `note_01.txt` 又做了修改，与暂存区的 `note_01.txt` 内容不一致了
