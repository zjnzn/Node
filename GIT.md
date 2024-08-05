# GIT

#### 用户

````git
git config --global user.name 'username'

git config --global user.email 'email@example.com'
````

#### 基本命令

```git
git init

git status

git add <filename>

git commit -m '描述'

git log [--oneline] [--graph]  [--all]

git show <commitID>

git reset --hard <commitID>

git reflog
```

#### .gitignore

```git
*txt

!asd.txt

test/

xxx/*.txt

xxx/**/*.txt
```

#### 分支

```git
git branch

git branch <name>

git branch -d <name>

git checkout <name>

git merge <name>

git diff
```

#### 变基

```git
git rebase <name>
```

#### 优选

```git
git cherry-pick <commit id>
```

#### 远程仓库

```git
git remote add 远程仓库名 远程仓库地址

git push 远程仓库名 本地分支名称[:远程分支名称]

token: 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
```

