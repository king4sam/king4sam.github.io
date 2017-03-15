---
layout: post
title: "jsuwp-4-34 functions are objects"
date: 2017-02-12 22:44:58 +0800
comments: true
categories: StudyNote javascript udemy
---

# 4-34 functions are objects

<!--more-->

## **bigword alert : first class functions**
- everything you can do with other types you can do with function
- ex: assign them to variables, pass them around, create them on the fly ...
- js is not the only language that has first class function

``` javascript function can has properties

function greet(){
  console.log('Hi');
}

greet.language = 'en';
console.log(greet.language);
// en

```

# 4-35 function statement and function expression

## **bigword alert : expression**
- a unit of code that results in a value
- statements just do the work, no return value

``` javascript statement and expression
// function statements
greet(); //runable because of hoisting

function greet (){
  console.log('Hi');
}

anonymousGreet(); //only variable is hoisted

// function expression
var anonymousGreet = function (){
  console.log('Hi');
}

```

``` javascript create function on the fly

function log(a){
  console.log(a);
  a(); //invoke it
}

log(function(){
  console.log('Hi');
})
```
