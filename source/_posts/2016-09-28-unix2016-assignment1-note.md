---
layout: post
title: "unix2016 assignment1 note"
date: 2016-09-28 23:51:08 +0800
comments: true
categories: unix2016
---

# Requirements

Implement your  own light-weight  wc utility, called  lwc.c,  in  C (not  C++)
<!--more-->
1. lwc only  supports  three options -l, -w, and –c; lwc assumes at  least one option  is  provided; lwc only process  files (ignore stdin)
2. lwc supports  multiple  options;  lwc ignore  the order of  options.  The no. lines is  always  printed first, followed by  the no. words and characters. run wc on Ubuntu  to  make  sure  that  your  outputs are identical to  it!
3. If  an  invalid option  or  filename  is  given,  lwc prints  the same  error message wc would  print to  stderr, and return  the same  non-zero  exit  status

# Implementation

1. 第一次知道有getopt()可以用 😂

``` c SYNOPSIS
#include <unistd.h>
int getopt(int argc, char * const argv[],const char *optstring);
```

另外有些 extern 的變數

- optind : The  variable optind is the index of the next element to be processed in argv.
- opterr : The calling program may prevent the error message by setting opterr to 0.(defualt value is 1)
- optopt : The variable optopt is set to the actual option character.

2. count的部分就沒有大問題，只有wordcount時注意一下連續空白就可以了

[link to assignment1](https://github.com/king4sam/nthu-unix2016/tree/master/assignment1)