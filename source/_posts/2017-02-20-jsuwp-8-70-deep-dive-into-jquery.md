---
layout: post
title: "jsuwp-8-69 ~ 8-72 Deep dive into jQuery"
date: 2017-02-20 16:39:33 +0800
comments: true
tags: StudyNote javascript udemy
---

<!--more-->

# 8-70 8-71 jQuert Part1、2

``` javascript jQuery Structure

// IIFE

(function(global, factory){
  ...

  // invoked factory
  return factory(global);
}(window, function(window, noglobal){
  version = "1.11.2",

  // Define a local copy of jQuery
  jQuery = function( selector, context ) {

    return new jQuery.fn.init( selector, context );
  },
  .
  .
  .

  // nickname for prototype
  jQuery.fn = jQuery.prototype ={
    ...
  };

  //Merge the contents of two or more objects together into the first object.
  jQuery.extend = jQuery.fn.extend = function() {
    ...

    // jQurry habe makeArray property which is a function
    makeArray: function( arr, results ) {
      var ret = results || [];

      if ( arr != null ) {
        if ( isArraylike( Object(arr) ) ) {
          jQuery.merge( ret,
            typeof arr === "string" ?
            [ arr ] : arr
          );
        } else {
          push.call( ret, arr );
        }
      }

      return ret;
    }

    ...
  }

  //use extend to add properties on jQuery
  jQuery.extend({...});

  // Sizzle CSS Selector Engine
  // another IIFE inside IIFE
  var Sizzle =(function (window){});

  // real init funciton
  init = jQuery.fn.init = function( selector, context ) {
    ...


    // this point to the empty object, created by calling new function
    // makeArray still return this
    return jQuery.makeArray( selector, this );
  }

  // set up the new object's prototype ctreated by new
  init.prototype = jQuery.fn;

  //window from line 8
  var
  // Map over jQuery in case of overwrite
  _jQuery = window.jQuery,

  // Map over the $ in case of overwrite
  _$ = window.$;

  // Expose jQuery and $ identifiers
  if ( typeof noGlobal === strundefined ) {
    window.jQuery = window.$ = jQuery;
  }

  return jQuery;

}));


```


---

# 8-73 jQuert Part3

## bigword alert : Method chaining
- calling one method after another, and each method affects the parent object.
- obj.method1().method2()

## how to implements  method chain
- functions return this

``` javascript jquery addClass function
addClass: function( value ) {
    var classes, elem, cur, clazz, j, finalValue,
      i = 0,
      len = this.length,
      proceed = typeof value === "string" && value;

    if ( jQuery.isFunction( value ) ) {
      return this.each(function( j ) {
        jQuery( this ).addClass( value.call( this, j, this.className ) );
      });
    }

    if ( proceed ) {
      // The disjunction here is for better compressibility (see removeClass)
      classes = ( value || "" ).match( rnotwhite ) || [];

      for ( ; i < len; i++ ) {
        elem = this[ i ];
        cur = elem.nodeType === 1 && ( elem.className ?
          ( " " + elem.className + " " ).replace( rclass, " " ) :
          " "
        );

        if ( cur ) {
          j = 0;
          while ( (clazz = classes[j++]) ) {
            if ( cur.indexOf( " " + clazz + " " ) < 0 ) {
              cur += clazz + " ";
            }
          }

          // only assign if different to avoid unneeded rendering.
          finalValue = jQuery.trim( cur );
          if ( elem.className !== finalValue ) {
            elem.className = finalValue;
          }
        }
      }
    }

    return this;
  }

```
