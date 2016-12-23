---
layout: post
title: "unix2016 assignment7 note"
date: 2016-12-22 10:49:25 +0800
comments: true
categories: unix2016
---

# Requirements

To implement Terminal Control and Signal Handling to support Job Control.

- Signal Handling: user can terminate the running process with Ctrl+C without quitting from your shell
- Background processes without resulting in zombies
- Foreground/Background Switching: Your shell is able to put the process to the background (“&”) and bring background process back to the foreground by “fg” command
- Built-in functions: jobs, fg
    - "Jobs" allows users to view all the processes
    - "fg" <shell_assigned_process_id>” (You will need to handle the id by yourself)

<!--more-->

#Implements

- set tsh controlling process as current foreground process

 The function tcgetpgrp() returns the process group ID of the foreground process group on the terminal associated to fd, which must be the controlling terminal of the calling process.

``` c SYNOPSIS https://linux.die.net/man/3/tcgetpgrp
int tcsetpgrp(int fd, pid_t pgrp);
```

- signal hanlding

	Control process should ignore terminate signal(SIGINT...)

	Control process set child process as foreground to access STDIN, so that child process would receive the signal from STDIN.

	Control process need to set signal handler for child process, preventing children becoming a zombie process

	there some special func defined
	- SIG_DFL is defalt handler
	- SIG_IGN is to ignore the signal

``` c SYNOPSIS https://linux.die.net/man/3/signal
void (*signal(int sig, void (*func)(int)))(int);
```

- job control

	implement a job queue to add/remove job while forking a new background process

- fg cmd

	control process set given jobid as foreground process and send SIGCONT to job to wake it

- extra note

	in SIGCHLD handler, use while to catch childe process's return status.

[links to assignment7](https://github.com/king4sam/nthu-unix2016/tree/master/assignment7)