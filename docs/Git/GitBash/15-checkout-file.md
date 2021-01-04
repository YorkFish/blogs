# 15. checkout file

## 1. 当前状态

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout --<file>..." to discard changes in workding directory)

        modified: README.md
        modified: note_01.md

no changes added to commit (use "git add" and/or "git commit -a")
```

### 说明

- 当前处于 `master` 分支
- 暂存区上一个版本的文件均已提交至仓库
- 此时暂存区的内容与仓库指向的版本的内容一致
- 红色的 <font color="red">modified</font>
    - `git status -s` 回馈的 <font color="red">M</font> 就是指 <font color="red">modified</font>
    - 这里表明工作区的 `README.md` 与 `note_01.txt` 发生了变动
- 提示中最后一行表明 `git add` 与 `git commit -a` 有相同的效果

### 补充

- Git 中常见的三种状态
  
    | 状态名 | 释义 |
    | :--- | :--- |
    | <font color="red">modified</font>    | 已修改 |
    | staged                               | 已暂存 |
    | <font color="green">committed</font> | 已提交 |

## 2. git checkout \-\- <file\>

- 命令的作用
    - 舍弃工作区的更改
    - 即，将工作区的内容拉回到暂存区的版本
    - 即，用暂存区的内容覆盖工作区的
- 虽说这条命令要少用，做实验嘛，不妨用一下
- `<file>` 可以是多个文件，用空格隔开即可

### 2.1 示意图

![](.\imgs\15-01_checkout_file_sketch_map.png)

### 2.2 覆盖操作

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git checkout -- README.md note_01.txt

York@DESKTOP MINGW64 /d/git/git_note (master)
$ git status
On branch master
nothing to commit, working tree clean
```

### 2.3 查看

- `note_01.txt`

    ```
    1. git init 初始化

    2. git status 查看

    3. git add <file> 将 <file> 加入暂存区

    ```

- `README.md`

    ```

    ```

#### 说明

- `note_01.txt` 少了一句 `4. git commit -m "<message>" 加入仓库`
- 这句话并不是消失了，而是当初就没存在过
- 之前的博文 《13 commit》 的 `2.3 骚操作` 中光顾着 `commit`，而在 `commit` 之前忘了 `add`
- `README.md`
    - 暂存区里的 `README.md` 本来就没写东西，所以是空白的
    - 开头的 <font color="red">modified</font> 是因为我当时变动了工作区的 `README.md`

## 3. git checkout \.

- 命令的作用：将暂存区中的内容尽数回滚给工作区

!!! danger
    此命令有危险！慎用！

### 3.1 操作

1. 对 `note_01.txt` 做些改动
2. 查看状态

    ```bash
    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ git status -s
     M note_01.txt
    ```

3. 使用 `checkout`

    ```bash
    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ git checkout
    M       note_01.txt

    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ git status -s
     M note_01.txt

    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ git checkout .

    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ git status
    On branch master
    nothing to commit, working tree clean
    ```

### 3.2 分析

- 仅仅使用 `git checkout` 的反馈：`note_01.txt` 处于“未追踪”状态
- 只有使用 `git checkout .` 才生效
