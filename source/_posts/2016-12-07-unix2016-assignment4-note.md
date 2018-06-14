---
layout: post
title: "unix2016 assignment4 note"
date: 2016-11-08 10:43:31 +0800
comments: true
tags: unix2016
---

#Requirements
Your tool will load this dictionary into memory, and tries to concatenate three words into the plaintext password candidate. Use the crypt library to find the actually password of a person. The TA will time how fast your code can break the password. The top 10% of the student will receive 2 bonus points.

<!--more-->
---

1. Your tool, say decrypt, that reads the hashed password from a file, and output the decrypted password. (sample test case can be downloaded from the iLms)

2. The password is composed of three random words from the given dictionary file.

3. You will need to check how to get a hashed string as explained during the lecture.

#Implementation

- more detail on user password

```
$6$naIJPKfO$SMkeSkFM36M6u3mZIyf2hAtt31WxuYtoTwLMjF9Fv49cprYPKtR1K88Ox5xvQdLdoBrAOmCnomRvaHc7VDiqQ0
```
```
$Algorithmid$Salt$Encryptedpassword
```

- algorithmid table

|ID  | Method|
|----|-------|
|1   | MD5|
|2a  | Blowfish (not in mainline glibc; added in some Linux distributions)|
|5   | SHA-256 (since glibc 2.7)|
|6   | SHA-512 (since glibc 2.7)|

- dictionary attack

[links to assignment4](https://github.com/king4sam/nthu-unix2016/tree/master/assignment4)