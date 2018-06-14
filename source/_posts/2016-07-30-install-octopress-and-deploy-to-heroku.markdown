---
layout: post
title: "Install octopress and deploy to heroku"
date: 2016-07-30 23:01:14 +0800
comments: true
tags:
- octopress
- rake
- heroku
---
部落開張啦~

以後疑難雜症或備忘錄就會記在這裡啦

首先就是架設這個部落格

上網找了蠻久才決定用octopress

剛好是適合programmer用的

用markdown寫文章，用git做版本控制，不用額外的db

而且是ruby做的，可以順便研究一下科科

<!--more-->

---

## install

基本上沒遇到問題

ruby環境之前的弄好了

只要照著[官網](http://octopress.org/docs/setup/)

        clone git clone git://github.com/imathis/octopress.git octopress
        cd octopress
        bundle install
        rake install

就完成了

## post article
rake 裡有寫好一些task可以用，要po文章可以用

		rake new_post["title"]

再用markdown語法，撰寫文章內章

		rake generate

會幫忙把.markdown檔編成html

並且放到public/blog裡

		rake preview

會在localhost:4000 可以預覽

之後再繼續研究有哪些方便的task可以用 😅

在這邊遇到的問題的rake aborted

		rake aborted!
		Gem::LoadError: You have already activated rake 11.2.2, but your Gemfile requires rake 10.5.0. Prepending `bundle exec` to your command may solve this.
因為我之前rail有裝過更新版的rake，目前似乎只能gem uninstall不符的版本，或是在指令前都加上bundle exec

例如

    bundle exec rake preview

##deploy to heroku
因為沒有放到github上，所以目前先用local git，直接push 到heroku上

這邊就不贅述


