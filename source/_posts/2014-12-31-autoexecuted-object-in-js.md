---
title: Autoexecuted object in JS
id: 607
categories:
  - JavaScript
date: 2014-12-31 13:00:14
tags:
---

 Sometimes you will need to create autoexecuted object (for example in case of load/document ready events). Have you tried to do it this way?

<pre class="line-numbers"><code class="language-javascript">(function() {
        // Elements
        var z;

        // Private methods
        var internalObj = {

            init: function() {
                console.log('init')
            }
        };

        // Autoinvoking constructor
        (function() {
            console.log('start');
            internalObj.init();

        })();

    })();</code></pre> 

## Autoexecuted object

So what will you do if you want to have external API to your "autoexecuted object"? You can do it this way:

<pre class="line-numbers"><code class="language-javascript">var auto = (function() {
        // Elements
        var z;

        // Private methods
        var internalObj = {

            init: function() {
                console.log('init')
            }
        };

        // Autoinvoking constructor
        (function() {
            console.log('start');
            internalObj.init();

        })();
        return { initObj: internalObj.init}

    })();

auto.initObj();</code></pre> 

Currently we are creating variable to which we are assigning an object. This object return an API with one method which is equal an internalObjec init method.

But what we can do if we do not ant to do it this way and we don't want to create any new object assigned to variable?

<pre class="line-numbers"><code class="language-javascript">(function() {
        // Elements
        var z;

        // Private methods
        var internalObj = {

            init: function() {
                console.log('init')
            }
        };

        // Autoinvoking constructor
        (function() {
            console.log('start');
            internalObj.init();

        })();
        this.init = internalObj.init;

    })();

init();</code></pre> 

So this.init = internalObj.init assigns to window (global) function a function from our internalObj - init.
