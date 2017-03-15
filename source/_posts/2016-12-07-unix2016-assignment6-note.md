---
layout: post
title: "unix2016 assignment6 note"
date: 2016-11-29 11:40:29 +0800
comments: true
categories: unix2016
---
#Requirements

We will write a tiny shell (tsh) command processor like sh, bash, or csh for single line commands. Your shell's main loop will display a prompt, read a line of input, and fork a child process to perform the indicated command.
<!--more-->
---

Required capabilities:

1. Ordinary commands, consisting of an executable program name and an optional list of arguments, run in a separate process.

2. Two built-in commands: cd and pwd

3. Background processing, when the last token in the command line is "&".

#Implementation

1. get user input

2. parse oneline cmd , create command argv &

3. if cmd is build-in cmd, call corresponding system call

4. if not, create a child process, and execvp the cmd
```
The exec family of functions replaces the current process image with a new process image.
```

5. if it is not a background process, use waitpid for childprocess

[links to assignment6](https://github.com/king4sam/nthu-unix2016/tree/master/assignment6)