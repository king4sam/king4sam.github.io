---
layout: post
title: "move blog to github.io"
date: 2016-08-04 23:46:00 +0800
comments: true
tags:
- github
- octopress
---

前兩天試著把部落格移到github.io

一是因為heroku改[免費dyno的使用方式](https://devcenter.heroku.com/articles/free-dyno-hours)

二還是想說有個遠端備份

---

<!--more-->

# 官方document

[here](http://octopress.org/docs/deploying/github/)

## 1. create new repo

Create a new Github repository and name the repository with the format username.github.io


## 2.  set up github

    rake setup_github_pages

輸入url後這指令還做了一些事

- Rename the remote pointing to imathis/octopress from 'origin' to 'octopress'
- Add your Github Pages repository as the default origin remote.
- Switch the active branch from master to source.
- Configure your blog's url according to your repository.
- Setup a master branch in the _deploy directory for deployment.

可以對照執行時的輸出

```
Added remote git@github.com:username/username.github.io.git as origin
Set origin as default remote
Master branch renamed to 'source' for committing your blog source files
rm -rf _deploy
mkdir _deploy
cd _deploy
Initialized empty Git repository in /Users/username/Desktop/GIT/octopress/_deploy/.git/
```

## 3. deploy blog

    rake generate
    rake deploy

除了像之前generate出靜態網頁外，還需要delpoy

一樣來看看這指令做了哪些事

- copy the generated files into _deploy/
- add them to git
- commit
- push them up to the master branch


```
## Deploying branch to Github Pages
## Pulling any updates from Github Pages
cd _deploy
cd -
rm -rf _deploy/index.html

## Copying public to _deploy
cp -r public/. _deploy
cd _deploy

## Committing: Site updated at 2016-08-02 08:54:10 UTC
*
## Pushing generated _deploy website
To git@github.com:username/username.github.io.git
 * [new branch]      master -> master
```

## 4. Custom Domains
沒申請過，等之後有再設定XD