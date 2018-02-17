---
title: iPhone fix - Problem with resizing of font during changing of orientation
  (portrait / landscape)
tags:
  - fix
  - iphone
id: 671
categories:
  - CSS
date: 2015-06-18 13:23:29
---

Have you got in past a problem of resizing text on iPhone? 
Here is the code which will prevent this behaviour:

<pre class="line-numbers"><code class="language-css"> html {
        -webkit-text-size-adjust: 100%; 
    }</pre></pre> 

Voila! Your text is now prevented while allowing user zoom.
