---
title: Breakpoint SASS. Configuration and how to use it.  (+ Gulp.js include paths)
id: 634
categories:
  - CSS
  - GitHub
  - SASS
date: 2015-05-06 17:30:55
tags:
---

Are you frustrated when you create media queries for elements in another file? Or maybe you are tired to define them each time?
If one of your answers is yes - try Breakpoint SASS. 

If you want to install it just type:

<pre class="lang:default decode:true " >bower install breakpoint-sass</pre> 

And you can start using it. 

## Configure with gulp

Im pretty lazy when Im coding and I dont want to repeat some steps - thats why I started using grunt and then gulp into my projects. But I dont want to write a full path to breakpoint.sass file into my includes in main sass file. So...

<pre class="lang:default decode:true " >gulp.task('sass', function() {
  gulp
  .src('./src/sass/*.scss')
  .pipe(sass({
    includePaths: ['./bower_components/breakpoint-sass/stylesheets']
  }))
  .pipe(gulp.dest('./dist/css'))

});</pre> 

This config will make it possible. It adds a path to your breakpoint.sass files at runtime so the include into sass file looks like this:

<pre class="lang:default decode:true " >@import "breakpoint"</pre> 

## Create first SASS file with Breakpoint

I love to use [foundation](http://foundation.zurb.com/) and @media queries defined into this project. So I used it as an good foundation into my project.

This is a list of variables used into my project based on [breakpoint](http://breakpoint-sass.com/). I hope it can help you creating your own media queries steps in your projects.
<pre class="lang:default decode:true " >// ********************
// Media Queries 
// ********************
$smallMax: 40em 
$mediumMin: 40.063em
$mediumMax: 64em

$mqSmall: max-width $smallMax
$mqMedium: $mediumMin $mediumMax</pre> 

Then with defined steps you can add breakpoint-sass to your project:
<pre class="lang:default decode:true " >h1, p.h1
	font:
		size: 60px
		weight: bold

	@include breakpoint($mqSmall)
		font:
			size: 30px

	@include breakpoint($mqMedium)
		font:
			size: 40px</pre> 

This will create CSS:
<pre class="lang:default decode:true " >h1, p.h1 {
  font-size: 60px;
  font-weight: bold; 
  }
  @media  (max-width: 40em) {
    h1, p.h1 {
      font-size: 30px; 
    } 
  }
  @media  (min-width: 40.063em) and (max-width: 64em) {
    h1, p.h1 {
      font-size: 40px; 
    } 
  }</pre> 

Ive been testing it into my current OS projects on Github so you can check how it works:
[https://github.com/fedojo/multigrid-css](https://github.com/fedojo/multigrid-css)
[https://github.com/fedojo/amelia-sg](https://github.com/fedojo/amelia-sg)

If you need any other information you can check the official website of breakpoint project: [http://breakpoint-sass.com/](http://breakpoint-sass.com/)