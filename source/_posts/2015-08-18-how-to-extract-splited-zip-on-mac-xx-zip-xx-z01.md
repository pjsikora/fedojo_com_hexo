---
title: 'How to extract splited zip on Mac (xx.zip, xx.z01,...)'
id: 690
categories:
  - Uncategorized
date: 2015-08-18 08:07:39
tags:
---

Yeah... stupid problem but I had it last time when I was working on my project.
It pretty easy when you are using window and for example Total Commander but when you are using Mac - it can make you a little suprise :)

problem:
You have files
name.zip
name.z01
name.z02
.
.
.

name.zNN

how to resolve it:
Combine files

<pre class="lang:default decode:true " >zip -s 0 name.zip --out combined.zip</pre> 

Than you can extract your archive with default ZIP app in Finder.