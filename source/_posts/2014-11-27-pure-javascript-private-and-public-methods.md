---
title: Pure JavaScript - Private and public methods
tags:
  - OO JS fundamentals
  - Vanilla JavaScript
id: 596
categories:
  - Uncategorized
date: 2014-11-27 09:28:12
---

Have you been creating your own classes in pure JavaScript? What if you neeed a private method? How to create them?

<pre class="line-numbers"><code class="language-javascript">var MyClass = (function() {
        function MyClass() {
        }

        var prvMethod = function() {
               console.log('method');
        };

        MyClass.prototype = {
            init: function() {
                console.log('init ');
                prvMethod();

            }

        };

        return MyClass;
    })();

var mc = new MyClass();
mc.init();
</code></pre> 

So finally you can access init() but cannot access prvMethod(). It has only access into MyClass() function scope.
