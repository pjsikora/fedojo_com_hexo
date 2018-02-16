---
title: 'Dealing with HTML5 video. '
tags:
  - html5
  - ogg
  - video
id: 248
categories:
  - HTML
  - JavaScript
date: 2014-07-14 14:48:49
---

Working with HTML5 video objects is currently on top of website trends. How to do it properly?
<!--more-->

How to include it in code:
<pre class="lang:default decode:true  ">&lt;video width="300" height="200" controls&gt;
       &lt;source src="url2file.mp4" type="video/mp4"&gt;
       &lt;source src="url2file.ogv" type="video/ogv"&gt;
       &lt;source src="url2file.webm" type="video/webm"&gt;
&lt;/video&gt;</pre>
In almost all cases you will need to add mp4 and ogv video.

In some cases you will need to get aspect ratio of you video. You cant use .height() or .width() functions from jQuery. You have to use .videoWidth and .videoHeight properties. Access to them is possible after triggered event loadedmetadata.
<pre class="lang:default decode:true ">var el = $('video');

el.bind("loadedmetadata", function () {
   var width = this.videoWidth;
   var height = this.videoHeight;
});</pre>
If you want to play video you will need to get adequate instantion.
<pre class="lang:default decode:true ">var el = $('video');
el.get(0).play();</pre>