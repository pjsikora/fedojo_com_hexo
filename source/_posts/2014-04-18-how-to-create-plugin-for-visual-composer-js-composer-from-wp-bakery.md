---
title: How to create component for Visual Composer (js_composer from WP Bakery)
tags:
  - js_composer
  - Shortcode
  - vc_map
  - Visual Composer
  - Visual Composer components
  - visual composer nested components
  - Wordpress
id: 75
categories:
  - CMS
  - WordPress
date: 2014-04-18 13:56:11
---

What is Visual Composer I think that I dont have to tell to anybody who is workin with WordPress. Its actually one of the most known commercial plugins for WordPress used in almost every template on [ThemeForest](http://themeforest.net/?ref=iclicksol "Theme Forest").

<!--more-->

All VIsual Composer elements are based on shortcodes. So when you need to make a new component you need to create a shortcode. Lets begin creation of our new Visual Composer element. In file functions.php of our theme lets write:
<pre class="lang:php decode:true">function sc_slide_func( $atts, $content) {
    extract( shortcode_atts( array(
        'bg_image' =&gt; 'bg_image',
        'header' =&gt; 'header'
    ), $atts ) );

    $end_content = ' &lt;div class="slide"&gt;';
    $end_content .= wp_get_attachment_image( 1 );
    $end_content .= '&lt;h2 class="text-center"&gt;'.$header.'&lt;/h2&gt;';  
    $end_content .= '&lt;/div&gt;'; 
    return $end_content;  
} 

add_shortcode( 'sc_slide', 'sc_slide_func');</pre>
**What is going on in this code?**
Firstly we are defining function with two parameters,

*   attributes of element - $atts (in WP editor for example [shortcode attr="1"]
*   content of element - $content (in WP editor [shortcode] our content [/shortcode] )
Function extract is changing our parameters from array $atts to variables which we can use in our returned code.

Function add_shortcode is binding our function to shortcode available in WP Editor.

&nbsp;

**How to connect it with Visual Composer
**When we have a simple (or more complex) shortcode available we can start binding it with Visual Composer. Write this code in functions.php:
<pre class="lang:php decode:true">vc_map( array(
    "name" =&gt; __("Component name", "js_composer"), // add a name
    "base" =&gt; "sc_slide", // bind with our shortcode
    "content_element" =&gt; true, // set this parameter when element will has a content
    "is_container" =&gt; true, // set this param when you need to add a content element in this element
    // Here starts the definition of array with parameters of our compnent
    "params" =&gt; array(
        array(
            "type" =&gt; "attach_image", // it will bind a img choice in WP
            "heading" =&gt; __("Image in background", "js_composer"),
            "param_name" =&gt; "bg_image",
        ),

        array(
            "type" =&gt; "textfield", // it will bind a textfield in WP
            "heading" =&gt; __("Header", "js_composer"),
            "param_name" =&gt; "header",
        )
    )
) );

// This function provides a functionality of adding content elements into element
class WPBakeryShortCode_SC_Slide extends WPBakeryShortCodesContainer {}</pre>
&nbsp;

&nbsp;

[![preview_4.0.5](http://fedojo.com/wp-content/uploads/2014/04/preview_4.0.5.jpg)](http://codecanyon.net/item/visual-composer-page-builder-for-wordpress/242431?ref=roqkai)