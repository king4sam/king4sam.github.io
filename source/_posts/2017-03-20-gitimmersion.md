---
layout: post
title: "Gitimmersion Notes"
date: 2017-03-20 14:34:51 +0800
comments: true
categories: git
---

之前用git時有些指令常常忘記，還來跳出去查一下
趁這次SS的機會，把常忘記的做個筆記

<!--more-->

---

# git command alias

```
vim ~/.gitconfig
/
[alias]
  co = checkout
  ci = commit
  st = status
  br = branch
  hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
  type = cat-file -t
  dump = cat-file -p
 */
```

# some useful pretty log config

```
git log --pretty=oneline --max-count=2
git log --pretty=oneline --since='5 minutes ago'
git log --pretty=oneline --until='5 minutes ago'
git log --pretty=oneline --author=<your name>
git log --pretty=oneline --all
git log --all --pretty=format:'%h %cd %s (%an)' --since='7 days ago'
git log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
```

# tag

git tag -d <tag>

# recover modified files

- before staging

```
checkout <file>
```

- before commit

```
git reset HEAD file //unstage the change.
git checkout file //
```

- after commit

```
- git revert HEAD // creating a new commit that reverses the unwanted changes.
- git reset --hard <hash>
```

``` plain quick fix on last commit
git commit --amend
```

They(bad commits) are still in the repository. It’s just that they are no longer listed in the master branch. If we hadn’t tagged them, they would still be in the repository, but there would be no way to reference them other than using their hash names.


- after push

**DON'T DO IT**

# move/rm file

``` plain
git mv file dir
/* equals
mv <file> <dir>
git add <dir> <file>
git rm <file>
*/
```

# Explore git internal
``` plain
// in .git
git cat-file -t <hash>
```

# merge vs rebase
Don’t use rebase …

- If the branch is public and shared with others. Rewriting publicly shared branches will tend to screw up other members of the team.
- When the exact history of the commit branch is important (since rebase rewrites the commit history).

# branch

``` plain
// show all branch
git branch -a
```

# Add a local branch that tracks a remote branch.

- 跟蹤分支是一種和某個遠端分支有直接聯繫的本地分支。
- 在跟蹤分支裡輸入 git push，Git 會自行推斷應該向哪個伺服器的哪個分支推送資料。
- 同樣，在這些分支裡運行 git pull 會獲取所有遠端索引，並把它們的資料都合併到本地分支中來

``` plain
git branch --track greet origin/greet
```

# Create a bare repository.
- a git repo withoud working directory
- It is usually used for sharing.

``` plain
cd ..
git clone --bare hello hello.git
ls hello.git
```

# Keeping a forked repo updated

```
//add remote repo
git remote add upstream <gitrepo>

// at master branch
git checkout master
git fetch upstream
git rebase upstream/master

```

[Refernce](http://gitimmersion.com)