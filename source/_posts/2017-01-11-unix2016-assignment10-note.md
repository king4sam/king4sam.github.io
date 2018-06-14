---
layout: post
title: "unix2016 assignment10 note"
date: 2017-01-11 17:36:45 +0800
comments: true
tags: unix2016
---

# Requirements

1. Write a program to determine your system's byte ordering. Explain how does it work and present your test results.

2. Write a client program and a server program to continuously report the number of processes currently running on a specified host (UNIX) computer. Make sure your server supports multiple concurrent clients and handle socket-related exceptions.

<!--more-->

---

# Implements

1. byte ordering
- 用casting，將int(32bit) cast 成 char(8bit)
- 檢查char 是哪兩個byte，就能知道系統的byte ordering

2. socket
- sysinfo contains procs,

``` c get current # process
struct sysinfo si;
sysinfo(&si);
printf("num of process : %d", si.proc);
```

- server

1. getaddrinfo(), traversal the result list to get a available socket
2. socket() create a socket descriptor
3. bind() bind portnumber with the socket descriptor
4. listen() listen on the port
5. accept() wait for a connection
6. after accept a connection, create a new process to handle clients
7. write sth to the socket descriptor

- client
1. getaddrinfo(), traversal the result list to get a available socket
2. socket() create a socket descriptors
3. connect() connect to remote host
4. read() read from the socket descriptor

[links to assignment10](https://github.com/king4sam/nthu-unix2016/tree/master/assignment10)