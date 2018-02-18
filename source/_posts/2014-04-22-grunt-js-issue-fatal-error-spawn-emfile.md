---
title: 'Grunt.js issue : Fatal error: spawn EMFILE'
tags:
  - compass
  - 'Fatal error: spawn EMFILE'
  - Grunt.js
  - Grunt.js issue
  - yeoman
id: 90
categories:
  - Compass
  - Grunt.js
  - Yeoman
date: 2014-04-22 20:54:24
---

Im still workin on grunt.js task runner. And in the last project I had a problem after which I had to restart my grunt server.

<pre class="lang:default decode:true">Fatal error: spawn EMFILE</pre>
That was a problem which occures in my terminal.

How to fix it?

Write it in your console:
<pre class="lang:default decode:true">ulimit -n 1000</pre>
Your problem should be fixed. If the count 1000 is too big for your OS try lower value.

&nbsp;
