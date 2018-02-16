---
title: Wordpress custom post type
tags:
  - custom post type
  - Wordpress
id: 113
categories:
  - CMS
  - WordPress
date: 2014-05-05 21:46:41
---

Sometimes you will need some more functionalities than CMS has in default configuration.  Wordpress gives you simple way to create your own content type based on post/page content type. How to do it?

<!--more-->

Add this code to your functions.php file and... voila!

<pre class="lang:php decode:true">function create_post_type() {
    $labels = array(
        'name'               =&gt; _x( '&lt;Name of your post types&gt;', 'post type general name' ),
        'singular_name'      =&gt; _x( '&lt;Name of singular element&gt;', 'post type singular name' ),
        'add_new'            =&gt; _x( 'Add New', 'book' ),
        'add_new_item'       =&gt; __( 'Add New Element' ),
        'edit_item'          =&gt; __( 'Edit Element' ),
        'new_item'           =&gt; __( 'New Element' ),
        'all_items'          =&gt; __( 'All Elements' ),
        'view_item'          =&gt; __( 'View Element' ),
        'search_items'       =&gt; __( 'Search Elements' ),
        'not_found'          =&gt; __( 'No Element found' ),
        'not_found_in_trash' =&gt; __( 'No Element found in the Trash' ),
        'parent_item_colon'  =&gt; '',
        'menu_name'          =&gt; 'Element'
    );

    $args = array(
        'labels'        =&gt; $labels,
        'description'   =&gt; 'Holds our products and product specific data',
        'public'        =&gt; true,
        'menu_position' =&gt; 5,
        'supports'      =&gt; array( 'title', 'editor', 'thumbnail', 'excerpt', 'comments', 'type', 'post-formats' ), // which features custom post type should provide 
        'has_archive'   =&gt; true,
    );

    register_post_type( 'element', $args );
}

function my_taxonomies_elements() {
    $labels = array(
        'name'              =&gt; _x( 'Elements Categories', 'taxonomy general name' ),
        'singular_name'     =&gt; _x( 'Element Category', 'taxonomy singular name' ),
        'search_items'      =&gt; __( 'Search Element Categories' ),
        'all_items'         =&gt; __( 'All Element Categories' ),
        'parent_item'       =&gt; __( 'Parent Element Category' ),
        'parent_item_colon' =&gt; __( 'Parent Element Category:' ),
        'edit_item'         =&gt; __( 'Edit Element Category' ),
        'update_item'       =&gt; __( 'Update Element Category' ),
        'add_new_item'      =&gt; __( 'Add New Element Category' ),
        'new_item_name'     =&gt; __( 'New Element Category' ),
        'menu_name'         =&gt; __( 'Element Categories' ),
    );
    $args = array(
        'labels' =&gt; $labels,
        'hierarchical' =&gt; true,
    );

    register_taxonomy( 'element_category', '  portfolio', $args );
}

add_action( 'init', 'create_post_type' );
add_action( 'init', 'my_taxonomies_elements',0);</pre>