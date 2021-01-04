# 23. 解决冲突

1.  定稿 `note_01.txt`

    ```
    1. git init 初始化

    2. git status 查看

    3. git add <file> 将 <file> 加入暂存区

    4. git commit -m "<message>" 加入仓库

    5. master round 3.1

    ```

2. `add` + `commit`

    ```bash
    York@DESKTOP MINGW64 /d/git/git_note (master|MERGING)
    $ git add note_01.txt

    York@DESKTOP MINGW64 /d/git/git_note (master|MERGING)
    $ git commit -m "note_01.txt v3.1"
    [master 6ca5df5] note_01.txt v3.1

    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ 
    ```

3. 目前的情况

    ![](./imgs/23-01_now_status.png)

4. `log` 命令的补充
  
    ```bash
    York@DESKTOP MINGW64 /d/git/git_note (master)
    $ git log --oneline --graph
    *   6ca5df5 (HEAD -> master) note_01.txt v3.1
    |\
    | * 61383e0 (conflict) conflict, note_01, add sentence
    * | 5b2e65a master, note_01, add sentence
    |/
    * ad80cbd Modification of note_01.txt
    * a6e6c95 add dev_01.txt to dev branch
    * 3f06ce7 (origin/master) add will_be_deleted.txt
    * 67dc44a add sentence 3 add sentence 4
    * 9884432 add note_01.txt
    * 6cc65c6 add README.md
    ```
