# 8. 合并分支

## 情形一

### 示意

```
o -> o ----> o
     v       ^
      -> o ->
```

### 操作

1. 点击仓库名
2. 点击 <kbd>Compare & pull request</kbd>

    ![](./imgs/08-01_compare&pull_request.png)

3. 填写下图 `1` 与 `2`，并点击 <kbd>Create pull request</kbd>，想偷懒也可以不写

    ![](./imgs/08-02_create_pull_request.png)

4. 页面跳转如下

    ![](./imgs/08-03_merge_pull_request1.png)

5. 点击 <kbd>Merge pull request</kbd>
6. 过度画面

    ![](./imgs/08-04_merge_pull_request2.png)

7. 完成画面

    ![](./imgs/08-05_confirm_merge.png)

8. 点击 <kbd>confirm merge</kbd> 结束操作

    ![](./imgs/08-06_after_confirm_merge.png)

### 图像

![](./imgs/08-07_history_graphic.png)

## 情形二

### 示意

```
o -> o -> o -> o
     v         ^
       -> o ->
```

### 操作

1. 再建一个分支

    ![](./imgs/08-08_create_new_branch.png)

2. 小发现：若分支名出现空格，GitHub 会自动用 `-` 填补
3. 写入内容

    ![](./imgs/08-09_add_a_few_words_fourth.png)

4. `Commit` (branch: Algorithm-problem)

    ![](./imgs/08-10_commit_changes.png)

5. 切到主分支，并在主分支上做更改：刚才是添加内容，现在是更改标题

    ![](./imgs/08-11_change_words.png)

6. `Commit` (branch: master)

    ![](./imgs/08-12_commit_again.png)

### 图像

![](./imgs/08-13_history_graphic.png)

### 后续操作

1. <kbd>Compare & pull request</kbd>
2. <kbd>Create pull request</kbd>
3. <kbd>Merge pull request</kbd>
4. <kbd>Confirm merge</kbd>

### 文件内容

![](./imgs/08-14_master_effect.png)
 
### 图像

![](./imgs/08-15_history_graphic.png)

***

## 补充

- **情形二**弱化了“解决冲突”
- 详见 <a href="https://yorkfish.github.io/blogs/git/gitbash/23-conflict-resolution/" target="_blank">23 解决冲突</a>
