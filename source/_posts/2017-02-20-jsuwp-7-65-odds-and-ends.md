---
layout: post
title: "jsuwp-7-65 ~ 7-68 Odds and Ends"
date: 2017-02-20 15:29:15 +0800
comments: true
categories: StudyNote javascript udemy
---

<!--more-->

# 7-65 Initialization

- use literal notaion to initialization
- convenient for testing
- js engine will check syntax for you

``` javascript simple initialization

var people = [
  {
    firstname : 'John',
    lastname : 'Doe',
    address : [
      '111 Main St.',
      'others'
    ]
  },
  {
    firstname : 'Jane',
    lastname : 'Doe',
    greet : function (){
      return 'Hi ';
    }
  }
]

```
---

# 7-66 typeof instanceof

-  typeof : return the type name in String

- some unexpected result : [], undefined, null

- instanceof : find in deeper prototype chain, check if the type in the chain

``` javascript

var a = 3;
console.log(typeof a);

var b = "Hello";
console.log(typeof b);

var c = {};
console.log(typeof c);

var d = [];
console.log(typeof d); // weird!
console.log(Object.prototype.toString.call(d)); // better!

function Person(name) {
    this.name = name;
}

var e = new Person('Jane');
console.log(typeof e);
console.log(e instanceof Person);

console.log(typeof undefined); // makes sense
console.log(typeof null); // a bug since, like, forever...

var z = function() { };
console.log(typeof z);

```

---

# 7-67 Strict Mode

- optional
- must be in the top of file or top of the function
- not every js engine implement strict mode in the same way

[strict mode reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)

- 可能問題
當多個js files合併時(produciton常用)，最開始的js file若使用了strict mode，則後面的files都會受到影響
不能保證其它lib都遵守strict mode

``` javascript one circumstance that strict mode helps
//'use strict';

function logNewPerson(){
  //'use strict';

  var person2;
  persom2 = {};
  console.log(persom2);
}

var person;

persom = {};
console.log(persom);

```