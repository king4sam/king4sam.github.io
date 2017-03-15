---
layout: post
title: "jsuwp-4-30 Objects and Functions"
date: 2017-02-12 00:06:26 +0800
comments: true
categories: StudyNote javascript udemy
---

<!--more-->

# 4-30 Objects and the DOT

-  \[ \] (computed member access) is a operator
-  . (dot) is a operator too
-  both has left-to-right asscociativity
- dot is recommended

``` javascript computed member access

var person = new Object();

person["firstname"] = "Tony";
person["lastname"] = "Alicea";

var firstNameProperty = "firstname";

console.log(person);
console.log(person[firstNameProperty]);


```

``` javascript dot operator

var person = new Object();

person["firstname"] = "Tony";
person["lastname"] = "Alicea";

console.log(person.firstname);

person.address = new Object();
person.address.stree = "111 Main St.";
person.address.city = "New York";
person.state = "NY";

```

# 4-31 Object and object literal

- {} is NOT a operator

``` javascript object literal

/*
var person {};
= var person = new Object();
*/

var Tony = {
  firstname : 'Tony',
  lastname : 'Alicea',
  address : {
    stree : '111 Main St.',
    city : 'New York',
    state : 'NY'
  }
};

function gree(person){
  console.log('Hi ' + person.firstname);
}

greet(Tony);

// creating object on the fly
greet({
  firstname : 'Mary',
  lastname : 'Doe'
});


```