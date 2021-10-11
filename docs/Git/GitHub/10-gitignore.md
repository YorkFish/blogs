# 10. gitignore

## 1. 简单说明

```
过滤
/mtk/             过滤整个文件夹
*.zip             过滤所有.zip文件
/mtk/do.c         过滤某个具体文件

添加文件
!*.zip
!/mtk/one.txt

文件夹 mtk 下只要 one.txt
/mtk/
!/mtk/one.txt
```

## 2. 语法

### 配置语法

- 以 `/` 开头表示目录
- `*` 通配多个字符
- `?` 通配单个字符
- `[]` 包含单个字符的匹配列表
- `!` 表示 不忽略/跟踪 匹配到的文件或目录

- git 对于 \.ignore 配置文件是按行从上到下进行规则匹配的，
- 这意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效

### 示例说明

- `fd1/*`
    - 忽略目录 fd1 下的全部内容
    - 注意：不管是根目录下的 /fd1/ 目录，还是某个子目录 /child/fd1/ 目录，都会被忽略
- `/fd1/*`
    - 忽略根目录下的 /fd1/ 目录的全部内容

```
/*
!.gitignore
!/fw/bin/
!/fw/sf/

说明：
忽略全部内容，除了
    .gitignore 文件
    根目录下的 /fw/bin/ 和 /fw/sf/ 目录
```

## 3. 添加方式

### 方式一

- 在工程文件夹内手动或命令生成文件，可以在根目录，也可以在某个文件夹内
- 路径是相对当前 `.gitignore` 所在文件夹而言的
- 命令可以是 `echo “*.class” >.gitignore`
    - `>>` 类似 `a`
    - `>` 类似 `w`
    - 第一次 echo 可以生成文件

### 方式二

- `git config --global core.excludesfile ~/.gitignore`
    - `~/.gitconfig` 文件中会出现 `excludesfile = /home/{user}/{file}/.gitignore`

### 方式三

- 在工程目录下找到 `.git/info/exclude`，把要排除的文件写进去

## 4. 举例

```
# 此为注释，将被 Git 忽略
*.a  # 忽略所有 .a 结尾的文件
!lib.a  # 但 lib.a 除外

/TODO  # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/  # 忽略 build/ 目录下的所有文件
doc/*.txt  # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

## 5. 说明

- `.gitignore` 只能忽略那些原来没有被 track 的文件，
- 如果某些文件已经被纳入了版本管理中，则修改 `.gitignore` 是无效的
- 解决方法：先把本地缓存删除（改变成未 track 状态），然后提交

```
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```
