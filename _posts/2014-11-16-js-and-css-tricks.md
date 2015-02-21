---
layout: post
title: JS & CSS Tricks [Update]
date: 2014-11-16 11:05:50
---

##JavaScript##

**Strip HTML Tags in JavaScript**

``` javascript
var StrippedString = OriginalString.replace(/(<([^>]+)>)/ig,"");
```

**IIFE (Immediately Invoked Function Expression)**

``` javascript
// Anonymous function that has three arguments
(function(window, document, $) {

  // You can now reference the window, document, and jQuery objects in a local scope

})(window, document, window.jQuery); // The global window, document, and jQuery objects are passed into the anonymous function
```

**Find max value in an array**

``` javascript
var values = [1, 2, 3, 4, 5, 6, 7, 8];
var max = Math.max.apply(Math, values);
```

**Debug CSS layers**

``` javascript
// Try to type it in your browser console, and the different layers of HTML that there are in the web page will be highlighted in different colors.
[].forEach.call($$("*"),function(a){
  a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16)
})
```

***

##CSS##
