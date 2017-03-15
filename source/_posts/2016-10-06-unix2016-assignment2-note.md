---
layout: post
title: "unix2016 assignment2 note"
date: 2016-10-6 00:30:39 +0800
comments: true
categories: unix2016
---

# Requirements

In this assignment, you will need to write your own dup2 function that behaves the same way as the dup2 function described in Section 3.12.
<!--more-->
- Your dup2 must copy the file descriptor oldfd and use the newfd as the target fd.
- Make sure that the oldfd and the newfd point to the same file.
- The return file descriptor should be the new newfd that points to the file table of oldfd. If error occurs, you have to return -1.
- If newfd is not closed, you have to close the newfd before you copy the fds.
- Your dup2 should handle invalid file descriptors (please check out the valid range of file descriptors online) and others error status.
- Note that you can not use dup2, fcntl functions in your implementation.

---

# Implementation
1. KEYIDEA creates a copy of the file descriptor oldfd, using the lowest-numbered unused descriptor for the new descriptor.
所以我們重複呼叫dup，直到用到目標fd，再將之前多複製的fd關掉，就可以實作出dup2的功能

2. 呼叫sysconf(_SC_OPEN_MAX)太多次會crash，需將結果存下來

[link to assignment2](https://github.com/king4sam/nthu-unix2016/tree/master/assignment2)