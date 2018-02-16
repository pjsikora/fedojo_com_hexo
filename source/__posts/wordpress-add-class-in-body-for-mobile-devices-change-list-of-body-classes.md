---
title: WordPress - Add class in body for mobile devices / change list of body classes
tags:
  - body_class
  - Wordpress
id: 487
categories:
  - WordPress
date: 2014-10-07 15:28:25
---

Sometimes you need to extend your body classes list or simply add your custom list in body in your template. I needed this feature to add a "mobile" class for mobile devices into body. It provides me some better layout customization level. Here is how to do that.

    add_filter('body_class','my_body_classes');
    function my_body_classes($c) {

    	is_front_page()       		? $c[] = 'home'       	: null;
    	is_page_template('your-template.php')	? $c[] = 'your-template-class'	: null;
    	is_404()        		? $c[] = 'error404'     	: null; 
            wp_is_mobile()        		? $c[] = 'mobile'     	: null; 

    	return $c;
    }

[More about body_class ](http://codex.wordpress.org/Function_Reference/body_class)