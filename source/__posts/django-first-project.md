---
title: Django - first project. How to prepare environment.
tags:
  - django
  - python
id: 188
categories:
  - Django
  - Languages
  - Python
date: 2014-06-25 16:42:53
---

I like to search inspiration in other technologies. My last research was about speed and app performance. One of "fast" languages is Python. I heard about this language when I was a beginer in IT and wished to learn some programming language. This one was an example of languages 'good to learn programming'. Today its language used in apps like youtube, blogger and google.com. 

How to prepare your first project in Django? 

**1\. Install the latest Python from
**https://www.python.org/

2\. Install PIP
download this file : https://bootstrap.pypa.io/get-pip.py
and run it from console with: 

<pre class="lang:default decode:true " >sudo python get-pip.py</pre> 

Update if you need:

<pre class="lang:default decode:true " >pip install -U pip
</pre> 

For other systems check this [link](http://pip.readthedocs.org/en/latest/installing.html) (http://pip.readthedocs.org/en/latest/installing.html)

**3\. Install django **
<pre class="lang:default decode:true " >sudo pip install Django==1.6.5</pre> 

And check your installation

<pre class="lang:default decode:true " >python

import django
print(django.get_version())</pre> 

If you want to get out of python CLI push CTRL+D

**4\. Create Django project**
<pre class="lang:default decode:true " >django-admin.py startproject mysite</pre> 

This will create for you a folder mysite with Django project

Check your website on your localhost http://127.0.0.1:8000/