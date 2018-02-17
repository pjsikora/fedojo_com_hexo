---
title: Navigation HTML and CSS structure
id: 843
categories:
  - CSS
  - HTML
  - Uncategorized
date: 2016-06-12 12:55:04
tags:
  - CSS
  - HTML
  - Uncategorized
---

Few times I had explain how to create a good navigation structure, so here it comes:
<!--more-->

So good navigation should be based on ul &gt; li &gt; a structure wrapped into nav tag:
<pre class="lang:default decode:true">&lt;nav class="main_nav"&gt;
    &lt;ul&gt;
        &lt;li&gt;
            &lt;a href="link1"&gt;Link 1&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
            &lt;a href="link2"&gt;Link 2&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
            &lt;a href="link3"&gt;Link 3&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
            &lt;a href="link4"&gt;Link 4&lt;/a&gt;
        &lt;/li&gt;
    &lt;/ul&gt;
&lt;/nav&gt;</pre>
so when you have this structure you can create now the CSS basic code:
<pre class="lang:default decode:true">.main_nav {}
.main_nav ul {}
.main_nav li {}
.main_nav a {}</pre>
It is not complicated! Lets check the multilevel menu.

## Multilevel menu

This is most known issue in websites:
<pre class="lang:default decode:true">&lt;nav class="main_nav"&gt;
    &lt;ul&gt;
        &lt;li&gt;
            &lt;a href="link1"&gt;Link 1&lt;/a&gt;

            &lt;ul&gt;
                &lt;li&gt;
                    &lt;a href="link1"&gt;Link 1.1&lt;/a&gt;

                &lt;/li&gt;
                &lt;li&gt;
                    &lt;a href="link2"&gt;Link 1.2&lt;/a&gt;
                &lt;/li&gt;
                &lt;li&gt;
                    &lt;a href="link3"&gt;Link 1.3&lt;/a&gt;
                &lt;/li&gt;
                &lt;li&gt;
                    &lt;a href="link4"&gt;Link 1.4&lt;/a&gt;
                &lt;/li&gt;
            &lt;/ul&gt;
        &lt;/li&gt;
        &lt;li&gt;
            &lt;a href="link2"&gt;Link 2&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
            &lt;a href="link3"&gt;Link 3&lt;/a&gt;
        &lt;/li&gt;
        &lt;li&gt;
            &lt;a href="link4"&gt;Link 4&lt;/a&gt;

            &lt;ul&gt;
                &lt;li&gt;
                    &lt;a href="link1"&gt;Link 4.1&lt;/a&gt;
                &lt;/li&gt;
                &lt;li&gt;
                    &lt;a href="link2"&gt;Link 4.2&lt;/a&gt;
                &lt;/li&gt;
                &lt;li&gt;
                    &lt;a href="link3"&gt;Link 4.3&lt;/a&gt;
                &lt;/li&gt;
                &lt;li&gt;
                    &lt;a href="link4"&gt;Link 4.4&lt;/a&gt;
                &lt;/li&gt;
            &lt;/ul&gt;
        &lt;/li&gt;
    &lt;/ul&gt;
&lt;/nav&gt;</pre>
Now lets shortly introduce the CSS structre:
<pre class="lang:default decode:true ">.main_nav {}
.main_nav ul {} // all ul's
.main_nav li {} // all li's
.main_nav a {} // all a's

.main_nav ul ul {} // second level ul's and deeper
.main_nav li li {} // second level li's and deeper
.main_nav ul ul a {} // second level a's and deeper</pre>
&nbsp;
