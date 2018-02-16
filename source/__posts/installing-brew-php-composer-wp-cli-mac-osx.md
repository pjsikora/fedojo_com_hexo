---
title: 'Installing Brew, PHP, Composer, WP-CLI (MAC OSX)'
tags:
  - brew
  - composer
  - PHP
  - wp-cli
id: 558
categories:
  - WordPress
date: 2014-10-22 20:50:36
---

Firstly install Brew on your MAC
<pre class="lang:default decode:true ">ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"</pre>
Then install PHP
<pre class="lang:default decode:true">brew update
brew tap homebrew/dupes
brew tap homebrew/php
brew install composer</pre>
&nbsp;

If you have some problem with brew install composer (for example:

composer: Missing PHP53, PHP54, PHP55 or PHP56 from homebrew-php. Please install one of them before continuing
Error: An unsatisfied requirement failed this build.

)

... you have to install PHP in other version:
<pre class="lang:default decode:true ">brew install php54</pre>
Then install composer:
<pre class="lang:default decode:true ">brew install composer</pre>
Installation of WP-CLI:
<pre class="lang:default decode:true ">brew tap josegonzalez/homebrew-php
brew install wp-cli</pre>
&nbsp;

What is WP-CLI?
> **WP-CLI** is a set of command-line tools for managing [WordPress](http://wordpress.org/) installations. You can update plugins, set up multisite installs and much more, without using a web browser.
So WP-CLI makes your life easier each time you want to create new instance of WordPress, updete it or just update all plugins.

Full list of commands is available under this lin: [WP-CLI list of commands](http://wp-cli.org/commands/)