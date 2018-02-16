---
title: Automatic hyphens in FireFox
tags:
  - firefox
  - hyphens
id: 283
categories:
  - CSS
date: 2014-08-21 12:29:21
---

Into one of last projects I was dealing with automatic word breaking from FireFox. You cannot see this effect in any other browser.

<!--more-->

Quick fix:
<pre class="lang:css decode:true">* {
-webkit-hyphens: none;
-moz-hyphens: none;
-ms-hyphens: none;
hyphens: none;
}</pre>

Inspired by:
[https://developer.mozilla.org/en/docs/Web/CSS/hyphens](https://developer.mozilla.org/en/docs/Web/CSS/hyphens)