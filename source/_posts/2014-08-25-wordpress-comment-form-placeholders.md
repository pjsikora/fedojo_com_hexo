---
title: Wordpress - Comment form placeholders
tags:
  - comments form
  - form
  - Wordpress
id: 295
categories:
  - WordPress
date: 2014-08-25 21:42:46
---

How to add placeholders to comments form?
<!--more-->

<pre class="lang:php decode:true " >function fedojo_update_fields($fields)
{

    $commenter = wp_get_current_commenter();
    $req = get_option('require_name_email');
    $aria_req = ($req ? " aria-required='true'" : '');

    $fields['author'] =
        '&lt;p class="comment-form-author"&gt;
			&lt;input required minlength="3" maxlength="30" placeholder="' . __("Your Name*", "fedojo_theme") . '" id="author" name="author" type="text" value="' . esc_attr($commenter['comment_author']) .
        '" size="30"' . $aria_req . ' /&gt;
    	&lt;/p&gt;';

    $fields['email'] =
        '&lt;p class="comment-form-email"&gt;
    		&lt;input required placeholder="' . __("Your Email*", "fedojo_theme") . '" id="email" name="email" type="email" value="' . esc_attr($commenter['comment_author_email']) .
        '" size="30"' . $aria_req . ' /&gt;
    	&lt;/p&gt;';

    $fields['url'] =
        '&lt;p class="comment-form-url"&gt;
			&lt;input placeholder="' . __("Your Email*", "fedojo_theme") . '" id="url" name="url" type="url" value="' . esc_attr($commenter['comment_author_url']) .
        '" size="30" /&gt;
    	&lt;/p&gt;';

    return $fields;
}

add_filter('comment_form_default_fields', 'fedojo_update_fields');

function fedojo_comment_field($comment_field)
{

    $comment_field =
        '&lt;p class="comment-form-comment"&gt;
			&lt;textarea required placeholder="Enter Your Comment…" id="comment" name="comment" cols="45" rows="8" aria-required="true"&gt;&lt;/textarea&gt;
		&lt;/p&gt;';

    return $comment_field;
}

add_filter('comment_form_field_comment', 'fedojo_comment_field');</pre> 