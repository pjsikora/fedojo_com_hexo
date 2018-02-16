---
title: CSS @media print - guides
tags:
  - Bootstrap
  - CSS
  - Foundation
id: 182
categories:
  - CSS
  - Frameworks
  - Twitter Bootstrap
  - Zurb Foundation
date: 2014-06-24 08:49:30
---

Some of your product need printable version of webpage. What should you know about it?
<!--more-->
**1\. Backgrounds are not printed as default**
You have to remember about that because sometimes its easier to put image into background and add background-size: contain in CSS than using other options. In this case you need to create img visible only into printable version (check the 3rd point of this article)

**2\. Some frameworks (foundation) are adding hrefs to links**
How to remove hrefs from printable versions? 

<pre class="lang:default decode:true " >a[href]:after {
	content: none !important;
  }</pre> 

**3\. Some contents should be visible only on printable version and some should be hidden**
In Frameworks like Foundation you can use classes:

<pre class="lang:default decode:true " >.print-only
.hide-for-print
.show-for-print</pre> 

In Twitter Bootstrap:

<pre class="lang:default decode:true " >.visible-print
.hidden-print</pre> 

It is usable when you have some fixed elements and after scrolling you dont want to print them. Or sometimes you need to create (like in point 1) some fast alternatives for images on desktop and printable versions.

**4\. Animated elements**
It is easier to create one frame for this elements which are visible only on printable version. In sliders/banners you can take just one element to print.