---
layout: post
title: "about disqus..."
date: 2016-08-19 18:45:44 +0800
comments: true
categories:
- disqus
- octopress
---

困擾我很久的disqus終於在今天解開啦~

因為octopress原本就有嵌入disqus，只要在disqus官網註冊好，設定好shortname

在_config.yml 裡填入shortname就好了

但在githubio上卻一直無法載入成功

原本一直以為是code或設定的問題

但直到我今天打開chrome 的 console......

阿阿阿~因為githubio是提供 https

但octopress預設是載入http的 cdn，所以因為安全性載入失敗啊

只要改成https的cdn 就出現惹QQQQQ

耍蠢

只好紀念一下
