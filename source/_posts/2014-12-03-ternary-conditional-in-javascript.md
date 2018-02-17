---
title: Ternary conditional in JavaScript
tags:
  - javascript ternary
  - ternary
id: 603
categories:
  - JavaScript
date: 2014-12-03 23:36:44
---

Ternary conditional is really usefull when you are building your code. I was omitting it back in the days but currently Ive get back to use it more often. Especially because of its flexibility. In some cases it is hard to read long conditions but with good commented code you can easily describe how it works in detail.

Basic ternary conditional syntax:

<pre class="lang:default decode:true " >condition ? expr1 : expr2</pre> 

So if condition is true expr1 will be invoked if not expr2 will be invoked. This code equals:

<pre class="line-numbers"><code class="language-javascript">if (condition) {
  expr1
} else {
  expr2
}</code></pre> 

Basic usage is pretty easy so ... how to make it more useful?

For example you want to set value of variable. It is counter incremented by 1\. If this counter is bigger than length of array it should have 0 value. Else it should have value incremented by 1.

In "normal" code in which you are using if/else statement it should look:

<pre class="line-numbers"><code class="language-javascript">if (currentElement++ &gt;= this.length-1) {
 currentElement = 0;
}
else {
 currentElement++;
}</code></pre> 

As a ternary it looks like this:
<pre class="line-numbers"><code class="language-javascript">currentElement = (currentElement++ >= arr.length-1) ? 0 : currentElement++;</code></pre> 

Another example of ternary conditional in more complexed case:

<pre class="line-numbers"><code class="language-javascript">function fn5() {
  return 5;
}

function fn10() {
  return 10;
}

function go(settings) {
  var ret = (settings) ? fn5() : fn10();
  return ret;
}

go(); // will return 10
go(2); // will return 5</code></pre> 

Where can you use this code? For example in your class constructor when you want to pass to class an object with settings and check:
1. If object exists (and if its not add default values)
2. If object exists check if its values exists (and if not set default value)

Last piece of code gives you deeper analyse of overvwritting object properties based on ternary condition. Firstly we define defaultConfObj with all default values. Than we define confObj which will be used later as a configuration object. parseSettings function is comparing defaultConfObj with confObj. If some property is not defined in confObj it will be overwritten with default value. In function start we are checking if settings are setted. If yes settings are parsed if not default settings object is applied.

<pre class="line-numbers"><code class="language-javascript">var defaultConfObj = {
  element: '#wrapper',
  loop: true,
  navigation: false
};

var confObj = {
  element: '#myWrapper',
  loop: false
};

var parseSettings = function(s) {
  var newSettings = defaultConfObj;

  for (var prop in s) {
      newSettings[prop] = s[prop];
   }

  return newSettings;    
};

var start = function(settings) {  
  var objSettings = settings ? parseSettings(settings) : defaultConfObj;
  return objSettings;
};

console.log(start(confObj));</code></pre> 
