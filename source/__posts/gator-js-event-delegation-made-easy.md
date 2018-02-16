---
title: Gator.js - Event delegation made easy
tags:
  - Event Delegation
  - JavaScript
  - JavaScript libraries
id: 365
categories:
  - JavaScript
  - Libraries
  - Uncategorized
date: 2014-09-24 08:32:48
---

I was describing event delegation in previous posts. 
[JavaScript optimization – Event delegation](http://fedojo.com/javascript-optimization-event-delegation/ "JavaScript optimization – Event delegation")
[JavaScript optimization – Event delegation – jQuery style](http://fedojo.com/javascript-optimization-event-delegation-jquery-style/ "JavaScript optimization – Event delegation – jQuery style")
Why to use events delegation? As it is described on [Gator.js](http://craig.is/riding/gators "Gator.js") page

> improved performance/memory usage> 
> no need to re-attach events> 
> fewer functions to manage

Main plugin is adjusted for browsers IE9+, Chrome, Safari 5+, Firefox 3.6+. If you need to add lower versions of browsers you have to add a legacy.js file which is included in plugins folder.

Project page: [http://craig.is/riding/gators](http://craig.is/riding/gators "Gator.js - Gator is a simple event delegation library written in Javascript.")
Gator.js on GitHub: [https://github.com/ccampbell/gator](https://github.com/ccampbell/gator)