---
layout: post
title: JS & CSS Tricks (Keeps Updating)
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

***

##CSS##
