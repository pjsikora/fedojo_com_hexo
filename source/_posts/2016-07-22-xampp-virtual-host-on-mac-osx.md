---
title: XAMPP Virtual Host on MAC OSX
id: 878
categories:
  - XAMPP
  - Virtual Host
  - MAC OSX
  - Apache
date: 2016-07-22 19:51:20
tags:
  - XAMPP
  - Virtual Host
  - MAC OSX
  - Apache
---

This is very repeatable process to configure Virtual Hosts (especially when you need to work with PHP CMS'es like Drupal or WordPress). Lets gather all steps which you need to do to configure them:
<!--more-->

**1\. Configuration of Apache**
In file:
<pre class="line-numbers"><code class="language-javascript">/Applications/XAMPP/xamppfiles/etc/httpd.conf</code></pre> 

Uncommment:
<pre class="line-numbers"><code class="language-javascript">Include /Applications/XAMPP/etc/extra/httpd-vhosts.conf</code></pre> 

**2\. Add Virtual Host **
In file: 
<pre class="line-numbers"><code class="language-javascript">/Applications/XAMPP/xamppfiles/etc/httpd.conf</code></pre> 

Add:
<pre class="line-numbers"><code class="language-javascript">&lt;VirtualHost *:80&gt;
    ServerAdmin webmaster@dummy-host2.example.com
    DocumentRoot "/Users/piotr/_free/typo3_src-8.2.1"
    ServerName local.typo3
    ErrorLog "logs/dummy-host2.example.com-error_log"
    CustomLog "logs/dummy-host2.example.com-access_log" common
&lt;/VirtualHost&gt;
</code></pre> 

**3\. Add line redirection in hosts file**
In file:
<pre class="line-numbers"><code class="language-javascript">/etc/hosts</code></pre> 

Add your virtual host address:
<pre class="line-numbers"><code class="language-javascript">127.0.0.1 your.domain</code></pre> 

In case you have a problem:
> Access forbidden!
> 
> 
> You don't have permission to access the requested object. It is either read-protected or not readable by the server.
> 
> 
> If you think this is a server error, please contact the webmaster.

<pre class="line-numbers"><code class="language-javascript">&lt;VirtualHost *:80&gt;
    DocumentRoot "/your/path"
    ServerName local.typo3
    Options Indexes FollowSymLinks MultiViews
    &lt;Directory "/your/path"&gt;
        Allow from all
        Require all granted
    &lt;/Directory&gt;
&lt;/VirtualHost&gt;</code></pre> 

Restart your XAMPP and voila!
