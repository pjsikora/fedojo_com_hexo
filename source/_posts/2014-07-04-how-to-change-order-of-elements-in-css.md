---
title: How to change order of elements in CSS. Set order of elements in container.
tags:
  - CSS
  - HTML
  - Resposnive Web Design
id: 228
categories:
  - CSS
  - HTML
  - SASS
date: 2014-07-04 09:36:40
---

Its a tip for Responsive Web Design. When your desktop view is floated to left and in tablet/phone view you want to change order of elements and float right is not a good solution.

<!--more-->

HTML:
<pre class="lang:default decode:true">&lt;div class="container"&gt;

&lt;div class="el-2"&gt;&lt;/div&gt;
&lt;div class="el-1"&gt;&lt;/div&gt;

&lt;/div&gt;</pre>
SASS:
<pre class="lang:sass decode:true">.container
  display: -webkit-box
  display: -moz-box
  display: box
  -webkit-box-orient: vertical
  -moz-box-orient: vertical
  box-orient: vertical

  .el-1
    -webkit-box-ordinal-group: 1
    -moz-box-ordinal-group: 1
    box-ordinal-group: 1

  .el-2
    -webkit-box-ordinal-group: 2
    -moz-box-ordinal-group: 2
    box-ordinal-group: 2</pre>

CSS: 

<pre class="lang:css decode:true " >.container {
    display: -webkit-box;
    display: -moz-box;
    display: box;
    -webkit-box-orient: vertical;
    -moz-box-orient: vertical;
    box-orient: vertical;
}
.container .el-1 {
    -webkit-box-ordinal-group: 1;
    -moz-box-ordinal-group: 1;
    box-ordinal-group: 1;
}
.container .el-2 {
    -webkit-box-ordinal-group: 2;
    -moz-box-ordinal-group: 2;
    box-ordinal-group: 2;
}</pre> 