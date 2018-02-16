---
title: Wordpress - Visual Composer - Get image url from attach_image
tags:
  - Visual Composer
  - Wordpress
id: 299
categories:
  - WordPress
date: 2014-08-28 20:25:29
---

How to get image URL from attach_image in Visual Composer
<!--more-->

In VC_MAP definition you have:
<pre class="lang:default decode:true">array(
                "type" =&gt; "attach_image",
                "heading" =&gt; __("Image", "js_composer"),
                "holder" =&gt; "div",
                "class" =&gt; "",
                "param_name" =&gt; "image_url",
                "description" =&gt; __("Your desc", "js_composer")
            ),</pre>
In shortcode function you should have:
<pre class="lang:default decode:true"> $a = shortcode_atts(array(
            'image_url' =&gt; 'image_url',
        ), $atts);

        $img = wp_get_attachment_image_src($a["image_url"], "large");

        $imgSrc = $img[0];
</pre>
Previous article:
[How to create component for Visual Composer (js_composer from WP Bakery)
](http://fedojo.com/how-to-create-plugin-for-visual-composer-js_composer-from-wp-bakery/ "How to create component for Visual Composer (js_composer from WP Bakery)")