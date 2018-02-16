---
title: XAMPP Virtual Host on MAC OSX
id: 878
categories:
  - Uncategorized
date: 2016-07-22 19:51:20
tags:
---

This is very repeatable process to configure Virtual Hosts (especially when you need to work with PHP CMS'es like Drupal or WordPress). Lets gather all steps which you need to do to configure them:
<!--more-->

**1\. Configuration of Apache**
In file:
<pre class="lang:default decode:true " >/Applications/XAMPP/xamppfiles/etc/httpd.conf</pre> 

Uncommment:
<pre class="lang:default decode:true " >Include /Applications/XAMPP/etc/extra/httpd-vhosts.conf</pre> 

**2\. Add Virtual Host **
In file: 
<pre class="lang:default decode:true " >/Applications/XAMPP/xamppfiles/etc/httpd.conf</pre> 

Add:
<pre class="lang:default decode:true " >&lt;VirtualHost *:80&gt;
    ServerAdmin webmaster@dummy-host2.example.com
    DocumentRoot "/Users/piotr/_free/typo3_src-8.2.1"
    ServerName local.typo3
    ErrorLog "logs/dummy-host2.example.com-error_log"
    CustomLog "logs/dummy-host2.example.com-access_log" common
&lt;/VirtualHost&gt;
</pre> 

**3\. Add line redirection in hosts file**
In file:
<pre class="lang:default decode:true " >/etc/hosts</pre> 

Add your virtual host address:
<pre class="lang:default decode:true " >127.0.0.1 your.domain</pre> 

In case you have a problem:
> Access forbidden!> 
> 
> You don't have permission to access the requested object. It is either read-protected or not readable by the server.> 
> 
> If you think this is a server error, please contact the webmaster.

<pre class="lang:default decode:true " >&lt;VirtualHost *:80&gt;
    DocumentRoot "/your/path"
    ServerName local.typo3
    Options Indexes FollowSymLinks MultiViews
    &lt;Directory "/your/path"&gt;
        Allow from all
        Require all granted
    &lt;/Directory&gt;
&lt;/VirtualHost&gt;</pre> 

Restart your XAMPP and voila!