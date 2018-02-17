---
title: Image to HTML table
id: 1126
categories:
  - JavaScript
  - HTML
  - Node.js
  - Jimp
  - NPM
tags:
  - JavaScript
  - HTML
  - Node.js
  - Jimp
---

Few years ago when I was on Front trends I heard very interesting story about improvements in delivery of emailers. 
Every developer knows that it isn't easy to deliver complex email template. But one of the developers made a story about
images in email templates. It was related with visibility of company when email client has blocked images and he cannot
see the company logo because he can read only text from email. So how to deliver it without image? HTML TABLE!!!

It made me to create this simple script which will create a colorful HTML Table from source image.

<pre class="line-numbers"><code class="language-javascript">
    var Jimp = require("jimp");

    var imagePath = process.argv[2];

    function rgb2hex(rgb){
     rgb = rgb.match(/^rgba?[\s+]?\([\s+]?(\d+)[\s+]?,[\s+]?(\d+)[\s+]?,[\s+]?(\d+)[\s+]?/i);
     return (rgb && rgb.length === 4) ? "#" +
      ("0" + parseInt(rgb[1],10).toString(16)).slice(-2) +
      ("0" + parseInt(rgb[2],10).toString(16)).slice(-2) +
      ("0" + parseInt(rgb[3],10).toString(16)).slice(-2) : '';
    }

    Jimp.read(imagePath, function (err, image) {
        if (err) {
          console.log(err);
        } else {
          console.log('<table style="border-collapse: collapse; width: '+image.bitmap.width+'px; border: 0">');

          for (var j=0; j<image.bitmap.height; j++) {
            console.log('<tr>');

            for (var i= 0; i < image.bitmap.width; i++ ) {
              var pixelColor = Jimp.intToRGBA(image.getPixelColor(i, j));

              console.log('<td style="height: 1px; width: 1px; padding: 0; border: 0; background-color:');
              console.log( rgb2hex('rgb('+pixelColor.r+','+pixelColor.g+','+pixelColor.b+')') );
              console.log('"></td>');
            }
            console.log('</tr>');
          }

          console.log('</table>')
        }
    });
</code></pre>

## How to run it

All you need is to run this code inside folder with source code:
<pre class="line-numbers"><code class="language-javascript">node index.js images/logo.png > test.html</code></pre>

* images/logo.png - path of your image
* test.html - file in which HTML Table should land

Enjoy!

