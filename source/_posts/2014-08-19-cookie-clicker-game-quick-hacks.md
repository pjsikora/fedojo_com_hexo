---
title: 'Cookie clicker game - quick hacks :)'
tags:
  - Cookie clicker game
id: 276
categories:
  - Games
  - JavaScript
date: 2014-08-19 13:01:10
---

I remember about 6 months ago when I was playing [Cookie clicker](http://orteil.dashnet.org/cookieclicker/) game with my friend. We had a rat race who will have more cookies per second.
<!--more-->

How to click without clicking in this game? Just open JS console (ALT+CMD+I on Chrome) and insert this code:

<pre class="lang:js decode:true " >var interVal = setInterval(
  function(){ 
    var myEl = document.getElementById('bigCookie');  
    myEl.click();  }
, 1);</pre> 

It will click cookie each 1 milisecond... but... if you need more cookies on your account:

<pre class="lang:default decode:true " >var  gameEarn = setInterval(function() {
   Game.Earn(9999999999999999999999999999999999999999999);
}, 1);</pre> 

... and you will not be as fast as you can start buying any stuff :)

If you dont want to click any button to buy stuff:

<pre class="lang:default decode:true " >var buyStuff = setInterval(function() {
var myEl = document.getElementById('product0');  myEl.click();
var myEl = document.getElementById('product1');  myEl.click();
var myEl = document.getElementById('product2');  myEl.click();
var myEl = document.getElementById('product3');  myEl.click();
var myEl = document.getElementById('product4');  myEl.click();
var myEl = document.getElementById('product5');  myEl.click();
var myEl = document.getElementById('product6');  myEl.click();
var myEl = document.getElementById('product7');  myEl.click();
var myEl = document.getElementById('product8');  myEl.click();
var myEl = document.getElementById('product9');  myEl.click();
var myEl = document.getElementById('product10');  myEl.click();
},1);</pre> 

[![Screenshot 2014-08-19 14.57.34](http://fedojo.com/wp-content/uploads/2014/08/Screenshot-2014-08-19-14.57.34.png)](http://fedojo.com/wp-content/uploads/2014/08/Screenshot-2014-08-19-14.57.34.png)

Have a nice gameplay!