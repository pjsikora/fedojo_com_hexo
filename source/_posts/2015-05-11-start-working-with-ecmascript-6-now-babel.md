---
title: Start working with EcmaScript 6 now! Babel
tags:
  - babel
  - ecmascript 6
id: 639
categories:
  - JavaScript
  - Uncategorized
date: 2015-05-11 22:00:08
---

If you are a Front End Developer who loves Front End Stack and you want to be still up to date you have to start working with EcmaScript 6\. Why? This is the future of this language and tomorrow you have one day of delay with ES6:) 

Yes I can hear you now... "but this code is not working on old browsers" and ... now Im giving you a link [https://babeljs.io](https://babeljs.io) and 10 minutes to think. Dont hesitate!

So what you have to do?

## Install Babel on your machine!

<pre class="lang:default decode:true " >npm install -g babel</pre> 

And now you can easily write your first code. When you finish it you can compile your file and see how it works in browser.

Add compiler with watcher for your file: 
<pre class="lang:default decode:true " >babel script.js --watch --out-file script-compiled.js</pre> 

Now you can check how ES6 code compiles to ES5 code.

## Configure gulp to work with your ES6 files

Firstly install babel for gulp:
<pre class="lang:default decode:true " >npm install --save-dev gulp-babel</pre> 

Then add a task to your gulpfile.js

<pre class="lang:default decode:true " >var gulp = require("gulp");
var babel = require("gulp-babel");

gulp.task("default", function () {
  return gulp.src("src/app.js")
    .pipe(babel())
    .pipe(gulp.dest("dist"));
});</pre> 

And everything is working now as you wished.

## Work with ES6

There is a lot of tutorials about ES6 but you have to use it to learn it. Write your own tests to check what ES6 can give to you. It has a lot of new features so be ready for more fun and more reasearch. 

## My EcmaScript 6 tryout

Ive started to recreate my code in Geolocation.js. 
[https://github.com/fedojo/geolocation](https://github.com/fedojo/geolocation)

Here you can check the source in ES6:
[https://github.com/fedojo/geolocation-js/blob/master/src/src/Geolocation.es6.js](https://github.com/fedojo/geolocation-js/blob/master/src/src/Geolocation.es6.js)

Here is compiled code (by Babel)
[https://github.com/fedojo/geolocation-js/blob/master/build/Geolocation.es6.js](https://github.com/fedojo/geolocation-js/blob/master/build/Geolocation.es6.js)