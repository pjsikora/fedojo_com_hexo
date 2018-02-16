---
title: JavaScript - Loops
id: 815
categories:
  - Angular 2
  - JavaScript
  - Uncategorized
date: 2016-06-03 08:04:14
tags:
---

In my [previous post](http://fedojo.com/angular-2-rc1-pipes-and-http/) Ive described using Pipes with data loaded through Http request. First comment was about using loop:

> You should maybe think about using map and filter instead of for loops

Thanks **Angular2guy** for this comment because it made me curious (like Curiouse George : ) ) to check which loop should I use to make a code as fast as possible. Ive started with code originaly implemented in my Pipe:

**for in version:**
<pre class="lang:default decode:true " >if (args.length === 0) {
                console.time('firstLoop');

                for (let item of value) {
                     resultArray.push(item);
                }

                console.timeEnd('firstLoop');
}</pre> 

firstLoop: 0.025ms
firstLoop: 0.038ms
firstLoop: 0.028ms
firstLoop: 0.027ms
firstLoop: 0.027ms
firstLoop: 0.023ms
firstLoop: 0.080ms
firstLoop: 0.030ms
firstLoop: 0.026ms
firstLoop: 0.024ms

min: 0.023ms
max: 0.080ms
average: **0.0328** (0.025+0.038+0.028+0.027+0.027+0.023+0.080+0.030+0.026+0.024)/10

**map version:** 
<pre class="lang:default decode:true " >if (args.length === 0) {
                console.time('firstLoop');            

                value.map(function(item){
                     resultArray.push(item);
                });

                console.timeEnd('firstLoop');
}</pre> 

firstLoop: 0.189ms
firstLoop: 0.078ms
firstLoop: 0.154ms
firstLoop: 0.337ms
firstLoop: 0.065ms
firstLoop: 0.052ms
firstLoop: 0.080ms
firstLoop: 0.103ms
firstLoop: 0.163ms
firstLoop: 0.069ms

min: 0.052ms
max: 0.337ms
average: **0.129** (0.189+0.078+0.154+0.337+0.065+0.052+0.080+0.103+0.163+0.069)/10

**for version**
<pre class="lang:default decode:true " >if (args.length === 0) {
                console.time('firstLoop');

                for (var i=0, len = value.length; i&lt;len; i++) {
                    resultArray.push(value[i]);
                }

                console.timeEnd('firstLoop');
}</pre> 

firstLoop: 0.029ms
firstLoop: 0.025ms
firstLoop: 0.073ms
firstLoop: 0.016ms
firstLoop: 0.024ms
firstLoop: 0.046ms
firstLoop: 0.013ms
firstLoop: 0.015ms
firstLoop: 0.040ms
firstLoop: 0.018ms

min: 0.013ms
max: 0.073ms
average: **0.029** (0.029+0.025+0.073+0.016+0.024+0.046+0.013+0.015+0.040+0.018)/10

**Foreach**
Thanks [sunpietro](http://blog.piotrnalepa.pl/) for your comment. This is test with forEach loop.
<pre class="lang:default decode:true " >value.forEach(function(item) {
                    resultArray.push(item);
});</pre> 

firstLoop: 0.059ms
firstLoop: 0.070ms
firstLoop: 0.161ms
firstLoop: 0.061ms
firstLoop: 0.091ms
firstLoop: 0.058ms
firstLoop: 0.046ms
firstLoop: 0.072ms
firstLoop: 0.055ms
firstLoop: 0.101ms

min: 0.046ms
max: 0.161ms
average: **0.0774** (0.059+0.070+0.161+0.061+0.091+0.058+0.046+0.072+0.055+0.101)/10

**Summary**
After all this test we can see that for version is faster than the map and for in loops. I know that the context of using this functions can not be proper but in some cases the speed is very important. Maybe in future map() function will be optimized and will work faster. In this case "native" and oldschool methods are fastest.