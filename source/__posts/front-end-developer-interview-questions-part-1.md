---
title: Front End Developer Interview - Questions part 1
id: 696
categories:
  - Uncategorized
date: 2015-08-26 22:19:07
tags:
---

Headhunters are calling to you and want to check your skills as fast as possible. What are they asking about? Its rather simple questions but in some cases they know the tricky ones.

So what are they asking?

**Question: (CSS)**
Do you know the box model?
Please list elements of box model. 

This is the most fundamental knowledge about DOM and CSS.
Elements of box model:

*   margin
*   padding
*   border
*   content

So when you have a box described with CSS:

<pre class="lang:default decode:true " >.box {
width: 100px;
height: 200px;
border: 10px solid #000;
margin: 20px;
padding: 30px;
}</pre> 

what is total width/height and total height of the box?

total_width = width + border_left  + border_right + padding_left + padding_right + margin_left + margin_right

so in this case it is

total_width = 100 + 10 + 10 + 20 + 20 + 30 + 30 = 220 (px)

total_height = height + border_top  + border_bottom + padding_top + padding_bottom + margin_top + margin_bottom

so in this case it is:

total_height = 200 + 10 + 10 + 20 + 20 + 30 + 30 = 320 (px)

How can we omit problem of counting total width and height? Use a box-sizing in CSS. 

**Question: (CSS)**
_What is clearfix?_

This is mostly connected with floating elements in HTML / CSS. In case you have a container with floating elements you need to clear floatings in the last element of childrens of this container. In oldschool way:

HTML code: 
<pre class="lang:default decode:true " >&lt;div class="container"&gt;
&lt;div class="floating"&gt;&lt;/div&gt;
&lt;div class="floating"&gt;&lt;/div&gt;

&lt;div class="clearboth"&gt;&lt;/div&gt;
&lt;/div&gt;
</pre> 

CSS

<pre class="lang:default decode:true " >.container {}
.floating { width: 100px; height: 100px; float: left; }
.clearboth { clear: both }</pre> 

Now when you have :before and :after pseudoelements you dont need to waste one more tag in HTML for clearing floats. You just need to add a CSS to container:

<pre class="lang:default decode:true " >.container:before,
.container:after {
  content: "";
  display: table;
}

.container:after {
  clear: both;
}</pre> 

or create a standard reusable clearfix in same way:

<pre class="lang:default decode:true " >.container:before,
.clearfix:after {
  content: "";
  display: table;
}

.clearfix:after {
  clear: both;
}</pre> 

 