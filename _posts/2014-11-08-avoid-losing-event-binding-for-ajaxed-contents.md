---
layout: post
title: 防止事件绑定在 ajax 更新后失效
date: 2014-11-08 23:09:00
description: 防止事件绑定在 ajax 更新后失效
keywords: event binding,dojo,jquery
---
###问题：
最近在为网页元素添加点击事件，在测试过程中发现元素的点击事件在有 ajax 更新后失效。就是说假如为页面上的 `button` 加上一个点击事件：

```
$('button').on('click', function() {
  console.log('click');
});
```

之后页面可能通过 ajax 或者其他原因，新增了一些 `button` 元素，而这些新增的 `button` 是没有点击事件的。这是因为上面的 `$.on` 只为在代码执行时已经存在的元素绑定。

###解决办法：
通过 Google 我们可以很快找到解决办法，那就是用 `$.live`：

``` javascript
$('button').live('click', function() {
  console.log('click');
});
```

然而，由于[种种原因](http://api.jquery.com/live/)，`$.live` 已经被新版本的 jQuery 拿掉了。不过，`$.on` 也统合了 `$.live` 方法，所以，我们可以稍作改写：

``` javascript
$(document).on('click', 'button', function() {
  console.log('click');
});
```

这样，问题就真正解决了。

###Bonus:
由于本人项目使用 dojo，所以也得找出 dojo 版本的解决之道啊。

``` javascript
// dojo version 1.7
dojo.require('dojox.NodeList.delegate');

dojo.query(document).delegate("button", "onclick", function() {
  console.log("click");
});
```