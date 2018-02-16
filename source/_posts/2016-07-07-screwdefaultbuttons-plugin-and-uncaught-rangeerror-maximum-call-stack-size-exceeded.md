---
title: 'ScrewDefaultButtons plugin and '
Uncaught RangeError: Maximum call stack size exceeded""
id: 867
categories:
  - JavaScript
date: 2016-07-07 08:27:39
tags:
---

I was using a lot of plugins which can make my life easier when Im dealing with inputs especially checkboxes and radio buttons. One of the best plugins which Im been using is ScrewDefaultButtons.
<!--more-->

Ive started with this one:
<pre class="lang:default decode:true " >&lt;li&gt;
  &lt;label for="ch01"&gt;Lorem ipsum dolor&lt;/label&gt;
  &lt;input type="checkbox" id="ch01"/&gt;
&lt;/li&gt;</pre> 

When the plugin was invoked on this element with code:
<pre class="lang:default decode:true " >$('.product_filters input[type="checkbox"]').screwDefaultButtons({
    image: 'url("checkbox_sprite.png")',
    width: 15,
    height: 15
});</pre> 

The element label is inactive. This means that you can cannot change a value of checkbox described as a for attribute clicking on label. So Ive changed structure a little bit:
<pre class="lang:default decode:true">&lt;li&gt;
  &lt;label for="ch01"&gt;Lorem ipsum dolor
    &lt;input type="checkbox" id="ch01"/&gt;
  &lt;/label&gt;
&lt;/li&gt;</pre>

After this operation I had an error in my console:
<pre class="lang:default decode:true " >Uncaught RangeError: Maximum call stack size exceeded</pre> 

The problem was resolved with simple solution - removing the for attribute in label. 
<pre class="lang:default decode:true " >&lt;li&gt;
  &lt;label&gt;Lorem ipsum dolor
    &lt;input type="checkbox" id="ch01"/&gt;
  &lt;/label&gt;
&lt;/li&gt;</pre> 