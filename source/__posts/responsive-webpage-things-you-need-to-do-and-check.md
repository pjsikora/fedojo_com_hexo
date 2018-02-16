---
title: Responsive webpage - things you need to do and check. Mobile/Desktop/Wordpress
tags:
  - CSS
  - HTML
  - mobile
  - RWD
id: 255
categories:
  - CSS
  - HTML
  - JavaScript
  - WordPress
date: 2014-07-24 10:17:52
---

FEDojo steps which you should check on your RWD website before you go live.
<!--more-->

**Mobile**:
1\. Firstly you should prepare your HTML properly:
<pre class="lang:xhtml decode:true">&lt;meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"&gt;</pre>
2\. Hover animation in CSS - its rather getting user nervous, so try to avoid them.
3\. Hovers in JS - its creating one more step to get content
4\. Elements with fixed position - they are loosing them position when you click on any input.
5\. Retina ready - prepare your graphics with bigger size to display them properly on iPads, iPhones, new generations of Mac's
6\. Click elements should have proper size

**Desktop IE<=8**:
1\. Use [modernizer](http://modernizr.com/ "Modernizr") to check some if some functions are possible to use (video, audio, touch etc)
2\. Use one size of grid for IE<=8 - remember that there is no media queries possible to use
3\. Background-size property in CSS is not possible to use :)
4\. Use [CanIUse.com](http://caniuse.com/ "caniuse.com") to check your possibilities in browsers
5\. Console.log is not supported!

**Performance**:
1\. Use [ySlow](https://developer.yahoo.com/yslow/ "ySlow plugin") plugin to optimize your webpage

**Wordpress**:
1\. Use mobile detection to minimize number of requests and transfer ( [wp_is_mobile()](http://codex.wordpress.org/Function_Reference/wp_is_mobile "wp_is_mobile documentation") )
2\. Use minifying plugins ( [WP Minify](https://wordpress.org/plugins/wp-minify/ "WP Minify") )
3\. Use retina plugins ( [https://wordpress.org/plugins/wp-retina-2x/](https://wordpress.org/plugins/wp-retina-2x/ "WP-Retina-2x") )

Feel free to update this list in comments!