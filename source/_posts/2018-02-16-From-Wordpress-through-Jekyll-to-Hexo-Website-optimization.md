---
title: From Wordpress through Jekyll to Hexo - Website optimization
date: 2018-02-16 09:55:28
tags:
- optimisation
- wordpress
- jekyll
- hexo
- pingdom
- google
- psi
- page speed insights
- Search Engine Optimization
- SEO
- page optimisation
- page optimization
- requests minification
---

First of all I would like to say that I wanted to write this post for a very long time but... as always there is a common time issue.


## Main goals
Every optimisation needs to have basic goals. You want to hit some target. It can be better Search Engine Optimization. It can be basically speed optimization. From my perspective it was: <strong>SPEED!!!</strong>. So basic list of my tasks was:
1. Concantenate CSS and JS files (including minification of files)
2. Minify requests
3. Optimization of images
4. Serve static HTML files

## Concantenate CSS and JS files (including minification of files)
So firstly I tried to merge my CSS files into one request. It can be done with preprocessor (ie. SASS) but also you can use specific web tools like <a href="https://cssminifier.com/">https://cssminifier.com/</a> or you can use NPM modules in your Grunt/Gulp starter.

## Minify requests
Minification of reqests is rather easy to do because all you need to check is count of requests to server. In your browser you can check it in "Developer tools > Network". It lists your request to the server.

![Developer tools network - Website optimization](developer_tools_network.png "Developer tools network - Website optimization")

In previous step all requests for CSS and JS files were minified to one but you can do one more thing.
Merge CSS and JS content into served HTML. Additionally you can defne common lines of code and serve it in both (all) templates.
Specific one you can deliver additionally in selected templates.

Of course it has pros and cons. It doesnt create additional request to the server but in case of big files (CSS / JS) it wont be cached. In my case I chosen scenario that somebody can read my article and doesnt go to any other page and <strong>SPEED is the KING</strong>. Reader wants to read content and do not loose time for time load.

This creates for us a todo list in case of minification of requests

1. Minify CSS/JS
2. Divide common and template specific CSS/JS code
3. Merge code CSS/JS (common and specific) with HTML template

## Optimization of images
There is a lot of articles and tools which can describe it for you. I will stick mainly to the processes and possible scenarios:

* Optimization of images for web
* Merging images with HTML templates (changing image to base64 code)
* Remove images where it is possible to maximize page load

Same as in previous example we will need to decide if we want to stick to caching (images in this case) or not. If we decide that we wont cache them we should code them with base64 and include into code. If not we should create new request and add url in src attribute.

There is one more issue - size of file. In case of 5 images without base64 we have:

### Before appending base64 encoding
![Base64 image encoding - Before - Test 1](base64-before-001.png "Base64 image encoding - Before - Test 1")
![Base64 image encoding - Before - Test 2](base64-before-002.png "Base64 image encoding - Before - Test 2")
![Base64 image encoding - Before - Test 3](base64-before-003.png "Base64 image encoding - Before - Test 3")
![Base64 image encoding - Before - Test 4](base64-before-004.png "Base64 image encoding - Before - Test 4")
![Base64 image encoding - Before - Test 5](base64-before-005.png "Base64 image encoding - Before - Test 5")

### After appending base64 encoding
![Base64 image encoding - After - Test 1](base64-after-001.png "Base64 image encoding - After - Test 1")
![Base64 image encoding - After - Test 2](base64-after-002.png "Base64 image encoding - After - Test 2")
![Base64 image encoding - After - Test 3](base64-after-003.png "Base64 image encoding - After - Test 3")
![Base64 image encoding - After - Test 4](base64-after-004.png "Base64 image encoding - After - Test 4")
![Base64 image encoding - After - Test 5](base64-after-005.png "Base64 image encoding - After - Test 5")

## Before and after appending base64 encoding - comparison
For the straight comparison lets check max time, min time, average time, size of assets
In all cases the lower value the better

|                                 | Before        | After         | Diff                       | Winner        |
| ------------------------------- | ------------- | ------------- | -------------------------- | ------------- |
| Min Load time                   | 1.48s         | **1.39s**     | 0.09s                      | Base64        |
| Max Load time                   | **1.97s**     | 2.09s         | 0.12s                      | No Base64     |
| Avg Load time                   | **1.618s**    | 1.856s        | 0.238s	                   | No Base64     |
| DOMContentLoaded time min       | 0.182s        | 1.05s         | **0.868s (5 times!!!)**	   | No Base64     |
| DOMContentLoaded time max       | 0.439s        | 1.41s         | **0.971s (3 times!!!)**	   | No Base64     |
| DOMContentLoaded time avg       | 0.3036s       | 1.236s        | **0.9324s (4 times!!!)**	 | No Base64     |
| Size                            | **3.0MB**     | 3.7MB         | 0.7MB (+~20%)	             | No Base64     |

## Serve static HTML files
Every CMS engine with default settings deliveres content using engine. This means that if you want a page from some domain request goes to engine which delivers time of router/parser/database connection to deliver a content. There are of course plugins which can deliver static files. But in case of CMS the easies way to do it is check possibilities of ready systems. One of the most popular one is <a href="https://jekyllrb.com/">Jekyll</a>. It's Ruby based engine very easy to install and use. But with my love to JavaScript and after I moved to Jekyll I wanted to find some npm engine which will deliver same functionalities as in <a href="https://jekyllrb.com/">Jekyll</a>. And this way I found <a href="https://hexo.io/">Hexo</a>

### Page Speed Insights - Before (Wordpress) and After (<a href="https://jekyllrb.com/">Jekyll</a> / <a href="https://hexo.io/">Hexo</a>)
Before (Wordpress)
![Page Speed Insights - Mobile - Before full optimization](before/PageSpeed_Insights_mobile_before.png "Page Speed Insights - Mobile - Before full optimization")
![Page Speed Insights - Desktop - Before full optimization](before/PageSpeed_Insights_desktop_before.png "Page Speed Insights - Desktop - Before full optimization")

After (<a href="https://jekyllrb.com/">Jekyll</a> / <a href="https://hexo.io/">Hexo</a>)
![Page Speed Insights - Mobile - After full optimization](after/PageSpeed_insights_mobile_after.png "Page Speed Insights - Mobile - After full optimization")
![Page Speed Insights - Desktop - After full optimization](after/PageSpeed_insights_desktop_after.png "Page Speed Insights - Desktop - After full optimization")

### Web Page Test - Before (Wordpress) and After (<a href="https://jekyllrb.com/">Jekyll</a> / <a href="https://hexo.io/">Hexo</a>)
Before (Wordpress)
![Webpage test - Before full optimization](before/WebPagetest_before.png "Webpage test - Before full optimization")

After (<a href="https://jekyllrb.com/">Jekyll</a> / <a href="https://hexo.io/">Hexo</a>)
![Webpage test - After full optimization](after/WebPagetest_after.png "Webpage test - After full optimization")

### Pingdom - Website speed test - Before (Wordpress) and After (<a href="https://jekyllrb.com/">Jekyll</a> / <a href="https://hexo.io/">Hexo</a>)
Before (Wordpress)
![Pingdom Webpage test - Before full optimization](before/Pingdom-Website_speed_test_before.png "Pingdom Webpage test - Before full optimization")

After (<a href="https://jekyllrb.com/">Jekyll</a> / <a href="https://hexo.io/">Hexo</a>)
![Pingdom Webpage test - After full optimization](after/Pingdom-Website_speed_test_after.png "Pingdom Webpage test - After full optimization")

