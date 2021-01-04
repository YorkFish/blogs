# 22. 制造冲突（三）

!!! success
    这回是成功案例!

## 1. 目前的情况

![](.\imgs\22-01_now_status.png)

## 2. 切换分支

- 切到 `conflict` 分支

    ```bash
    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ git checkout conflict
    Switched to branch 'conflict'
    M       note_01.txt

    York@DESKTOP MINGW64 /d/git/git_note (conflict)
    $ 
    ```

- 上方最后一行：我当时在 `master` 分支的工作区对 `note_01.txt` 有所变动

## 3. 修改文本

- 修改 `conflict` 分支下的 `note_01.txt`

    ```
    1. git init 初始化

    2. git status 查看

    3. git add <file> 将 <file> 加入暂存区

    4. git commit -m "<message>" 加入仓库

    5. conflict round 3

    ```

## 4. add + commit

```bash
York@DESKTOP MINGW64 /d/git/git_note (conflict)
$ git add note_01.txt

York@DESKTOP MINGW64 /d/git/git_note (conflict)
$ git commit -m "conflict, note_01, add sentence"
[conflict 61383e0] conflict, note_01, add sentence
 1 file changed, 3 insertions(+), 1 deletion(-)
```

## 5. 切换分支

- 切回 `master` 分支

    ```bash
    York@DESKTOP MINGW64 /d/git/git_note (conflict)
    $ git checkout master
    Switched to branch 'master'
    Your branch is ahead of 'origin/master' by 2 commits.
      (use "git push" to publish your local commits)

    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ 
    ```

## 6. 修改文本

- 修改 `master` 分支下的 `note_01.txt`

    ```
    1. git init 初始化

    2. git status 查看

    3. git add <file> 将 <file> 加入暂存区

    4. git commit -m "<message>" 加入仓库

    5. master round 3

    ```

## 7. add + commit

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git add note_01.txt

York@DESKTOP MINGW64 /d/git/git_note (master)
$ git commit -m "master, note_01.txt, add sentence"
[master 5b2e65a] master, note_01.txt, add sentence
 1 file changed, 3 insertions(+), 1 deletion(-)
```

## 8. 合并

```bash
York@DESKTOP MINGW64 /d/git/git_note (master)
$ git merge conflict
Auto-merging note_01.txt
CONFLICT (content): Merge conflict in note_01.txt
Automatic merge failed; fix conflicts and then commit the result.

York@DESKTOP MINGW64 /d/git/git_note (master|MERGING)
$ 
```

!!! note "分析"
    - 产生冲突
    - `note_01.txt` 存在冲突
    - 必须手动解决冲突后再提交

## 9. 查看状态

```bash
York@DESKTOP MINGW64 /d/git/git_note (master|MERGING)
$ git status
On branch master
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:  note_01.txt

no changes added to commit (use "git add" and/or "git commit -a")

York@DESKTOP MINGW64 /d/git/git_note (master|MERGING)
$ git status -s
UU note_01.txt
```

## 10. 查看文本

- 打开 `note_01.txt`

    ```
    1. git init 初始化

    2. git status 查看

    3. git add <file> 将 <file> 加入暂存区

    4. git commit -m "<message>" 加入仓库

    <<<<<<< HEAD
    5. master round 3
    =======
    5. conflict round 3
    >>>>>>> conflict
    ```

!!! note "说明"
    - 冲突后，Git 会把冲突的地方列出来
    - 类似下方

```
<<<<<<< HEAD
...
=======
...
>>>>>>> branch_name
```
