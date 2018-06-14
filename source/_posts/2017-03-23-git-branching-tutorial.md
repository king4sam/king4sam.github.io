---
layout: post
title: "Git Branching Tutorial"
date: 2017-03-23 15:17:35 +0800
comments: true
tags: git
---

<!--more-->

# git reset vs git revert

- reset : rewriting the commit history. DON'T use it on pushed branches
- revert : creat a new commit, but it reverse changes.

<img src="{{root_url}}/images/studynotes/gitreset.png">

<img src="{{root_url}}/images/studynotes/gitrevert.png">


# git cherry-pick

- you would like to copy a series of commits below your current location (HEAD).

```
// master/HEAD is at C5
// pick C2 and C4 , add them to master
git cherry-pick C2 C4
```

<img src="{{root_url}}/images/studynotes/cherrypick.png">

- useage

<img src="{{root_url}}/images/studynotes/debug.png">

# git describe

- Describe a commit using the most recent tag reachable from it

# mixed

## situation

I want to do a slight modify on newImage, then move master to C3

- starting

<img src="{{root_url}}/images/studynotes/situation1_b.png">

- goal

<img src="{{root_url}}/images/studynotes/situation1_a.png">

- sol1

1. re-order the commits (rebase -i)

2. commit --amend to make the slight modification on newImage

3. re-order the commits back(git rebase -i)

4. move master(git branch -f master <target>)

- sol2

1. git cherry-pick C2

2. commit --amend to make the slight modification on newImage

3.  git cherry-pick C3

