---
title: Front End Developer arsenal - SASS. Installation and short manual.
tags:
  - CSS
  - FireSass
  - Ruby
  - SASS
  - SASS Compilation
  - SASS Debuging
  - SASS Mixins
  - SASS Variables
  - SCSS
id: 1
categories:
  - Compass
  - CSS
  - SASS
date: 2014-04-03 09:04:51
---

Have you ever been dreaming about variables in CSS code? Or maybe other functionalities like functions? The simplest way to have a variables in CSS is to work with preprocessor like SASS. <!--more-->

**1\. Ruby **

Firstly you need to know if you have Rudy on your machine.  Type in your terminal:
<pre>ruby -v</pre>
If execution of this comman something simillar to :

<span style="line-height: 1.5em;">ruby 2.0.0p247 (2013-06-27 revision 41674) [universal.x86_64-darwin13]</span>

<span style="line-height: 1.5em;">you can go to next step and start sass installation process. If not you have to install ruby interpreter. On Mac OSX its installed as default. On Windows you can use this link [http://www.rubyinstaller.org/](http://www.rubyinstaller.org/ "Ruby installer for windows")</span>

<span style="line-height: 1.5em;"> </span>

**2\. SASS installation**

If you have Ruby interpreter you can start SASS installation. Write it in your terminal:
<pre>sudo gem install sass</pre>
&nbsp;

&nbsp;

**3\. SASS short introduction**

**Compilation**

Compilation of file is pretty simple.
<pre class="lang:default decode:true">sass filename.sass:filename.css</pre>
This option will create for you filename.css CSS file from filename.sass SASS file.

If you dont want to repeat this option and need to add watcher just write:
<pre class="lang:default decode:true">sass --watch filename.sass:filename.css</pre>
When SASS file will be changed CSS file will be auto generated.

&nbsp;

**Compilation options**

For better debugging I recommend to use a FireSass in Firefox. Its available here [https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/](https://addons.mozilla.org/en-US/firefox/addon/firesass-for-firebug/ "FireSass"). Using it is available when you will compile file with this command:
<pre>sass --watch filename.sass:filename.css --debug-info</pre>
For production files I recommend to use compilation with minification mode.
<pre>sass filename.sass:filename.css --style compressed</pre>
&nbsp;

**4\. Usage**

**Variables**

Using variables is useful when you need to parametrise some elements. For example colours.
<pre class="lang:sass decode:true">$c_bg_gray: #252525 //bg color
$c_contact_blue: #00d8ff //font color

.nav a
 color: $c_bg_gray
 background: $c_contact_blue

.footer a
 color: $c_bg_gray
 background: $c_contact_blue</pre>
When you use a variables you dont have to search the code for colour. You just need to change value of variable and go ahead.

&nbsp;

**Mixins**

Sometimes you need to repeat some code with like function in programming language you can use mixin:
<pre class="lang:sass decode:true" title="Simple mixin">=borderRadius($time)
  -webkit-border-radius: $time
  -moz-border-radius: $time
  border-radius: $time

.roundBox
  +borderRadius($radius)</pre>
&nbsp;

&nbsp;