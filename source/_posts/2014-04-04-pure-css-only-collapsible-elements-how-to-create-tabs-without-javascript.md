---
title: Pure CSS only collapsible elements. How to create accordion without JavaScript
tags:
  - CSS
  - HTML
id: 34
categories:
  - CSS
  - HTML
date: 2014-04-04 12:00:46
---

Pure CSS collapsible (with on click) containers/elements/whateva.

[http://jsfiddle.net/u3Cjz/](http://jsfiddle.net/u3Cjz/)

CSS Code
<pre class="lang:default decode:true">&lt;div id="elem"&gt;&lt;/div&gt;

&lt;a href="#" class="par cac1"&gt;Tab 1&lt;/a&gt;
&lt;a href="#" class="par cac2"&gt;Tab 2&lt;/a&gt;
&lt;a href="#" class="par cac3"&gt;Tab 3&lt;/a&gt;

&lt;h1 class="zzz1"&gt;ELEMENT 1&lt;/h1&gt;
&lt;h1 class="zzz2"&gt;ELEMENT 2&lt;/h1&gt;
&lt;h1 class="zzz3"&gt;ELEMENT 3&lt;/h1&gt;</pre>
HTML Code
<pre class="lang:css decode:true">h1 {display: none; }

a.par:focus {color: red}
a.par.cac1:focus ~ h1.zzz1 { display: block; color: blue }
a.par.cac2:focus ~ h1.zzz2 { display: block; color: blue }
a.par.cac3:focus ~ h1.zzz3 { display: block; color: blue }</pre>
