---
layout: post
title: "unix2016 assignment3 note"
date: 2016-11-01 00:41:05 +0800
comments: true
categories: unix2016
---
# Requirements
<!--more-->
1. Write a utility like cp(1), say lcp, that copies a file containing holes, without copying the hole to the target file. Instead, your utility writes “\0” to fill those holes in the target file.
- lcp only needs to support basic copy feature; copying a file to another file. (usage : lcp <source_file> <destination_file>)
- Your output file should be identical to the original input file (size, content), but the block usage on the disk is different.
- You need to check how to create a file with holes as explained in Chapter 3.
- The test cases will be regular files, and you don’t have to handle any unusual exceptions.

2. In Section 4.22, our version of ftw, called ftw8.c, never changes its directory. Modify this routine so that each time it encounters a directory, it uses the chdir function to change to that directory, allowing it to use the filename and not the pathname for each call to lstat. When all the entries in a directory have been processed, execute chdir(".."). Compare the time consumed by this version and the version in the text book.
- Trace the ftw8 source code given by TA. (compile with “make ftw8”)
- Modify the code with chdir

# Implementation

1. 用read/write就符合需求了，唯一要注意的是lcp後的檔案權限也要跟原檔一樣

2. chdir()，不過給絕對路徑跟相對路徑在檔案數多時還是有效能的差距

[link to assignment3](https://github.com/king4sam/nthu-unix2016/tree/master/assignment3)