---
title: Grunt/Yeoman/Bower automated installation
tags:
  - automation
  - bower
  - Grunt.js
  - yeoman
id: 160
categories:
  - Grunt.js
  - Yeoman
date: 2014-05-28 22:02:32
---

Install nodejs
<!--more-->

&nbsp;

Then create file in terminal:

<pre class="lang:default decode:true " >touch npm-dependencies
chmod +x npm-dependencies
vi npm-dependencies</pre> 

<pre class="lang:default decode:true " >npm install -g grunt;
npm install -g grunt-cli;

npm install -g bower;
npm install -g yeoman;
npm install -g generator-generator;
npm install -g generator-jade;

npm install -g grunt-contrib-sass --save-dev;
npm install -g grunt-contrib-compass --save-dev;
npm install -g grunt-contrib-jade --save-dev;</pre>

then run the installation file:

<pre class="lang:default decode:true " >sudo ./npm-dependencies</pre> 

You can add all of your node dependencies into this file. It will automate a little your work when you will be creating new instance of node or you will reinstall your own system.