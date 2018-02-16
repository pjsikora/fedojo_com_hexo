---
title: >-
  module.js:340     throw err;           ^ Error: Cannot find module  / node.js
  error
tags:
  - Grunt.js
  - Grunt.js issue
  - node.js
id: 178
categories:
  - Uncategorized
date: 2014-06-22 22:18:59
---

Sometimes when you work with node.js apps (grunt, yeoman, gulp etc) you will see something like this error log:

&nbsp;
<pre class="lang:default decode:true">module.js:340
    throw err;
          ^
Error: Cannot find module '&lt;name of dependency&gt;'</pre>
&nbsp;

All you need to do is remember &lt;name of dependency&gt; and write:
<pre class="lang:default decode:true " >npm install &lt;name of dependency&gt;</pre> 

If you want to save dependancy in your package.json:
<pre class="lang:default decode:true " >npm install &lt;name of dependency&gt; --save-dev</pre> 