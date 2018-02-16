---
title: JavaScript optimization - Event delegation
tags:
  - Event Delegation
  - JavaScript optimization
id: 200
categories:
  - JavaScript
date: 2014-06-30 08:41:55
---

Dealing with events in JavaScript is easy when you are working with jQuery or other language. Adding .on() or addEventListener() to next object is one of the ways but when you have group of objects to which you are still adding new objects you have to repeat adding events to each new element. With Event delegation you can omit this problem.

HTML:
<pre class="lang:default decode:true">&lt;a id="add-button"&gt;Add&lt;/a&gt;
&lt;ul id="parent"&gt;
  &lt;li&gt;2&lt;/li&gt;
  &lt;li&gt;3&lt;/li&gt;
  &lt;li&gt;4&lt;/li&gt;
  &lt;li&gt;5&lt;/li&gt;
&lt;/ul&gt;
</pre>
JS:
<pre class="lang:default decode:true">document.getElementById("parent").addEventListener("click",function(e) {
	if(e.target &amp;&amp; e.target.nodeName.toLowerCase() == "li") {
    e.target.textContent = parseInt(e.target.textContent)+1;
	}
});

document.getElementById("add-button").addEventListener("click", function(e) {  
  var para = document.createElement("li");
  var node = document.createTextNode("0");
  para.appendChild(node);

  document.getElementById("parent").appendChild(para);
})</pre>
&nbsp;

CODEPEN:

See the Pen [FwftB](http://codepen.io/fedojo_com/pen/FwftB/) by FEDojo.com ([@fedojo_com](http://codepen.io/fedojo_com)) on [CodePen](http://codepen.io).

<script src="//codepen.io/assets/embed/ei.js" async=""></script>

As you can see in preview each element in &lt;ul id="parent"&gt; has click listener. Element &lt;a id="add-button"&gt; is adding new element which has event listener added. You dont have to repeat addEventListener() to each element so when you have more events added on element (for example mouseenter, mouseleave etc) they are added automaticaly.

How to do that in jQuery:
&nbsp;
<pre class="lang:default decode:true">$( "#parent" ).on( "click", "li", function( event ) {
    // here your code
});</pre>