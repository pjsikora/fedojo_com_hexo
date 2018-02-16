---
title: Wordpress - Adding css/js file to specific template
tags:
  - Wordpress
id: 339
categories:
  - CMS
  - WordPress
date: 2014-09-11 10:46:25
---

In some project I needed to add styles and scripts which will not affect any other template.
<!--more-->

How to do it easiest way? In your functions.php:
<pre class="lang:default decode:true ">function fedojo_enqueue()
{
    if ( is_page_template( 'path-to-template/template-file-name.php' ) ) {
        wp_enqueue_style('style-sheet-name', get_template_directory_uri() . '/your/path/style.css', array(), '0.1');

    }
}

add_action('wp_enqueue_scripts', 'fedojo_enqueue');</pre>

Short legend:
path-to-template - here you have to set a path to your template file. 