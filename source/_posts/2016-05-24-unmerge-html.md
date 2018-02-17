---
title: UnMerge HTML
id: 761
categories:
  - JavaScript
date: 2016-05-24 09:19:45
tags:
---

When you are creating a email template the most known process after develop process is merging CSS into HTML. This process is creating style attribute and in value of it is adding declarations from class which is added to described element. Finally it removes class section. But what if you need the process which will get styles and create classes from it? Ive made a simple UnMerge script:

&nbsp;

&nbsp; 
<pre class="line-numbers"><code class="language-javascript">var onLoaded = function () {
  var query = document.querySelectorAll('[style]'),
      len =   query.length,
      arrayOfStyles = [],
      textNode = '',
      arrayOf = [],
      lenOfStyles = null,
      style = document.createElement("style");

  for (var i = 0; i < len; i++) {
    // Eliminate duplicates
     if (arrayOf.indexOf(query[i].getAttribute('style')) == -1) {
        var newStyle = {
            name: 'class-' + i,
            value: query[i].getAttribute('style'),
        };

        arrayOf.push(query[i].getAttribute('style'));
        arrayOfStyles.push(newStyle);
     }
  }

  lenOfStyles = arrayOfStyles.length;
  for (var j = 0; j < lenOfStyles; j++) {
     var arr = document.querySelectorAll('[style="' + arrayOfStyles[j].value + '"]');

     for (var z =0, l= arr.length; z < l; z++) {

       var el = arr[z];

       el.className += arrayOfStyles[j].name;
       el.removeAttribute('style');
     }

     textNode += '.' + arrayOfStyles[j].name + '{' + arrayOfStyles[j].value + '}';
  }

  var t = document.createTextNode(textNode);
  style.appendChild(t);

  document.body.appendChild(style);
}

document.addEventListener('DOMContentLoaded', onLoaded, false);</code></pre> 

Just append it to your HTML file and in style tag it will gather all classes. The HTML markup will be updated too (style attribute will be removed and class will be added). 
