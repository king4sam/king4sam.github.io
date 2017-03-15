---
layout: post
title: "jsuwp-9-73 ~ 9-80 Let's build a Framework/library"
date: 2017-02-25 01:04:51 +0800
comments: true
categories: StudyNote javascript udemy
---


# 9-73 Requirements

- Greeter
- input : firstname lastname and optional language
- output : formal and informal greeting sentence
- language support English and Spanish
- reusable
- just G$() to call (no 'new')
- support jQuery(give selector, add greeting sentence to the selected element)

``` javascript Greeter.js

;(function (global, $){
  // trick , avoid the problem caused by other lib that doesn't end with semicolon

  // trick to use our lib without new
  // function declare, it is not actually run
  // so we can set Greeter.init later
  var Greeter = function(firstName,lastName,language){
    return new Greeter.init(firsname,lastname,language);
  }

  // setup prototype of greeter
  Greeter.prototype = {
    fullName : function(){
      return this.firstName + ' ' + this.lastName;
    },

    validate : function (){
      if (supportedLangs.indexOf(this.language) === -1){
        throw 'Invalid language';
      }
    },

    greeting : function(){
      return greetings[this.language] + ' ' + this.firstName + '!';
    }

    formalgreeting : function(){
      return formalgreetings[this.language] + ', ' + this.fullName;
    }

    greet : function (formal){
      var msg ;
      if(formal){
        msg = formalgreeting();
      }
      else{
        msg = greeting();
      }

      if(console){
        console.log(msg);
      }

      return this;
    },

    log : function (){
      if(console){
        console.log(logMessages[this.language] + ' : ' + this.fullName());
      }
      return this;
    }

    setLang : function(lang){
      this.language = lang;

      this.validate();

      return this;
    },

    // support jQuery
    HTMLGreeting : function(selector, formal){
      if(!$){
        throw 'jQuery isnot loaded';
      }
      if(!selector){
        throw 'Missing jQuery selector';
      }
      var msg;
      else{
        msg = this.greeting()
        $(selector).html = msg;

        return this;
      }
    }

  };

  // available in init function because of closeure
  // but these var can't be access from global
  var supportedLangs = ['en','tw'];

  var greetings = {
    en : 'Hello',
    tw : '哈囉'
  };

  var formalgreetings = {
    en : 'Greetings',
    tw : '你好'
  };

  var logMessages = {
    en : 'Logged in',
    tw : '登入'
  }

  // real constructor
  Greeter.init = function (firstName,lastName,language){
    // safe this
    // point to the object created by new ()init
    var self = this;

    // setting default value
    var self.firstName = firstName || 'DefaultFirstname';
    var self.lastName = lastName || 'DefaultLastname';
    var self.language = language || 'en';

    self.validate();
  }

  //setup prototype chain of the object created by new init()
  Greeter.init.prototype = Greeter.prototype;

  //expose greeter to the world
  global.Greeter = global.G$ = Greeter;

}(window,jQuery));

```