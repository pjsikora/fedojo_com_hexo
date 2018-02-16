---
title: >-
  How to disable automatic loading of jquery and jquery-migrate in WordPress.
  Deregister script.
tags:
  - Wordpress
id: 239
categories:
  - WordPress
date: 2014-07-10 09:00:56
---

When you want to have a full customizing powers on WordPress or you want to change version of included jQuery you will need to deregister script.

<!--more-->

Its the function which you can call in file functions.php: 
<pre class="lang:default decode:true " >&lt;?php wp_deregister_script( $handle ); ?&gt;</pre> 

So when you want to deregister jquery you just need to call this function with right parameter: 
<pre class="lang:default decode:true " >&lt;?php wp_deregister_script( 'jquery' ); ?&gt;
&lt;?php wp_deregister_script( 'jquery-migrate' ); ?&gt;</pre> 

It will disable automatic loading of scripts.