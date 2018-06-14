---
layout: post
title: "jsuwp-4-32 Framework aside: Faking Namespace"
date: 2017-02-12 00:43:18 +0800
comments: true
tags: StudyNote javascript udemy
---

<!--more-->

# 4-32 Faking Namespace

## **bigword alert : Namespace**
- a container for variables and functions

``` javascript

greet = 'Hello!';
greet = 'Hola!';

// greet collide
console.log(greet);

var english = {};
var spanish = {};

english.greet = 'Hello!';
spanish.greet = 'Hola!';

english.greetings.greet  = 'Hello'; // cannot creating on the fly

/*
var english = {
  greeting : {
    basic : 'Hello!'
  }
};
 */


```