---
title: JavaScript optimization – Event delegation - jQuery style
tags:
  - Event Delegation
  - JavaScript optimization
id: 236
categories:
  - JavaScript
date: 2014-07-09 12:20:31
---

In one of previous posts I described event delegation. This time its time to make it better in jQuery.

<!--more-->

What if you have a multiple click events? (or any other events) Code can look like this:

<pre class="lang:default decode:true " >container
      .on('click','.elem1', function(){ // your body})
      .on('click','.elem2', function(){ // your body})</pre> 

Ive recreated it like this: 
<pre class="lang:default decode:true " >container.on({
                click: function(e) {
                    var t = $(e.target);

                    if (t.hasClass('elem1')) {
                       // your body
                    }

                    if (t.hasClass('elem2')) {
                        // your body
                    }
                }
            })</pre> 