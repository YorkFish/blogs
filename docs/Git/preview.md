??? example "config"
    - `git config --global user.name "York"`
    - `git config --global user.email "york@email.com"`
    - `git config --global color.ui true`
    - `git config --global alias.st status`

??? example "clone"
    - `git clone git@github.com:YorkFish/hello-world.git`
    - `git clone git@github.com:YorkFish/hello-world.git --depth=1`

??? example "remote"
    - `git remote`
    - `git remote -v`
    - `git remote add origin git@github.com:YorkFish/hello-world.git`
    - `git remote rm origin`

??? example "push"
    - `git push -u origin <branch>`
    - `git push origin <branch>`

??? example "connect"
    - `ssh -T git@github.com`
    - `ssh-keygen -t rsa -C "york@email.com"`

??? example "init"
    - `git init`

??? example "status"
    - `git status`
    - `git status -s`

??? example "add"
    - `git add <file/folder>`
    - `git add .`

??? example "commit"
    - `git commit`
    - `git commit -m "<message>"`
    - `git commit -am "<message>"`
    - `git commit --amend`

??? example "log"
    - `git log`
    - `git log --oneline`
    - `git log --oneline --graph`
    - `git log --oneline --graph --decorate --all`
    - `git reflog`

??? example "reset"
    - `git reset --hard HEAD@{n}`
    - `git reset --hard HEAD^`
    - `git reset --hard HEAD~`
    - `git reset --hard HEAD~~`
    - `git reset --hard HEAD~10`
    - `git reset --hard <hash_id>`
    - `git reset HEAD <file/folder>`

??? example "restore"
    - `git restore [--worktree] <file/folder>`
    - `git restore --staged <file/folder>`
    - `git restore --staged --worktree <file/folder>`
    - `git restore --source <branch> <file/folder>`

??? example "checkout"
    - `git checkout -- <file/folder>`
    - `git checkout .`

??? example "diff"
    - `git diff <file>`
    - `git diff --cached <file>`
    - `git diff HEAD <file>`
    - `git diff <hash_id> <file>`
    - `git diff --cached <hash_id> <file>`
    - `git diff <hash_id1> <hash_id2> <file>`

??? example "rm"
    - `git rm <file>`
    - `git rm --cached <file>`
    - `git rm -r <folder>`

??? example "branch"
    - `git branch`
    - `git switch <branch>`
    - `git checkout <branch>`
    - `git switch -c <branch>`
    - `git checkout -b <branch>`
    - `git checkout -b <branch> origin/<branch>`
    - `git branch -d <branch>`
    - `git branch -D <branch>`

??? example "merge"
    - `git merge <branch>`
    - `git merge --no-ff -m "<message>" <branch>`

??? example "stash"
    - `git stash`
    - `git stash list`
    - `git stash apply` + `git stash drop`
    - `git stash pop`

??? example "pull"
    - `git pull`
    - `git branch --set-upstream-to=origin/<banch> <branch>`

??? example "rebase"
    - `git rebase <branch>`

??? example "tag"
    - `git tag`
    - `git tag <tag>`
    - `git tag <tag> <hash_id>`
    - `git tag -d <tag>`
    - `git tag -a <tag> -m "<message>" <hash_id>`
    - `git show <tag>`
    - `git push origin <tag>`
