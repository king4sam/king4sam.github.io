---
layout: post
title: "theme安裝"
date: 2016-08-05 10:52:06 +0800
comments: true
categories:
- octopress
- theme
---
在安裝theme時遇到蠻多問題的

所以再開一篇專門來討論
<!--more-->
---

#theme

先上網找到第三方octopress 的theme

[範例](https://github.com/octothemes/cyan#applying-the-cyan-theme-to-your-blog)

clone 下來後通常會是個sass sourse兩個資料夾

安裝指令

    rake install[themename]

再進一步進去rakefile看做了哪些事

```
task :install, :theme do |t, args|
  if File.directory?(source_dir) || File.directory?("sass")
    abort("rake aborted!") if ask("A theme is already installed, proceeding will overwrite existing files. Are you sure?", ['y', 'n']) == 'n'
  end
  # copy theme into working Jekyll directories
  theme = args.theme || 'classic'
  puts "## Copying "+theme+" theme into ./#{source_dir} and ./sass"
  mkdir_p source_dir
  cp_r "#{themes_dir}/#{theme}/source/.", source_dir
  mkdir_p "sass"
  cp_r "#{themes_dir}/#{theme}/sass/.", "sass"
  mkdir_p "#{source_dir}/#{posts_dir}"
  mkdir_p public_dir
end
```

default是安裝classic這個theme
大致上只是將sass 跟source複製出來
有自已改過樣式的話可以自行將這兩個資料夾備份




