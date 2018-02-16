---
title: How to load font in CSS / Embed Webfonts in CSS / Base64
tags:
  - base64
  - CSS
  - optimize
  - optimize CSS
id: 157
categories:
  - CSS
  - SASS
date: 2014-05-22 11:18:22
---

Sometimes you will need to make your website faster. One of methods (not optimal in all cases of course) is to add base64 content into CSS files. For example images and fonts.

&nbsp;

This is normal font-face definition:
<pre class="lang:css decode:true">@font-face {
  font-family: 'FontName';
  font-style: normal;
  font-weight: 400;
  src: local('FontName-Regular'), 
       url('FontName-Regular.woff') 
       format('woff');
}
</pre>
In command line change woff to base64 file:
<pre class="lang:default decode:true">base64 -i FontName.woff -o FontName.woff.b64</pre>
Then in CSS file change:
<pre class="lang:default decode:true">src: url(data:font/woff;base64,&lt;content from file FontName.woff.b64&gt;)</pre>
And tadam! It works!