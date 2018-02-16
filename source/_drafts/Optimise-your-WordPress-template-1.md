---
title: Optimise your WordPress template
id: 1087
categories:
  - Uncategorized
tags:
---

I needed to optimise my WordPress template
<!--more-->

## Disable WP-Smiley ( img.wp-smiley, img.emoji + script )

Do you recognise this code included to your HTML in WordPress?

    img.wp-smiley,
    img.emoji {
    	display: inline !important;
    	border: none !important;
    	box-shadow: none !important;
    	height: 1em !important;
    	width: 1em !important;
    	margin: 0 .07em !important;
    	vertical-align: -0.1em !important;
    	background: none !important;
    	padding: 0 !important;
    }
    		`</pre>
    You can easy disable it using this two lines:
    <pre>`remove_action('wp_head', 'print_emoji_detection_script', 7);
    remove_action('wp_print_styles', 'print_emoji_styles');

## Disable wp-embed

<pre></pre>