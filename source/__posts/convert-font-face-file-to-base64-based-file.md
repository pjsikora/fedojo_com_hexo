---
title: Convert font-face file to base64-based file
tags:
  - '@font-face optimisation'
  - CSS
  - font-face
  - optimise CSS
id: 170
categories:
  - Bash
  - CSS
  - SASS
date: 2014-06-03 21:38:32
---

I was watching my apps with ySlow and found some additional requests. My app still asked server for a font files. As much @font-face as much requests.
After that decided to write some simple bash script to automate base64 encoding process for all devices.

<pre class="lang:default decode:true " >function fontface2base64() {
    fontName=$1
    fontFace=$2   

    WOFF=`base64 $fontName.woff`
    EOT=`base64 $fontName.eot`
    SVG=`base64 $fontName.svg`
    TTF=`base64 $fontName.ttf`

    echo @font-face {
    echo font-family: \'$fontFace\'\;

    echo src: url\(\'data:font/eot\;base64:$EOT\'\)\;

	echo src: url\(\'data:font/eot\;base64:$EOT\'\) format\(\'embedded-opentype\'\),\n
	echo  url\(\'data:font/woff\;base64:$WOFF\'\) format\(\'woff\'\),\n
	echo  url\(\'data:font/ttf\;base64:$TTF\'\) format\(\'truetype\'\),\n
	echo  url\(\'data:font/svg\;base64:$SVG\'\) format\(\'svg\'\)\;

    echo font-weight: normal\;
	echo font-style: normal\;
    echo }    

}</pre> 

Its short begining of this function. It can be expended as you only wish.