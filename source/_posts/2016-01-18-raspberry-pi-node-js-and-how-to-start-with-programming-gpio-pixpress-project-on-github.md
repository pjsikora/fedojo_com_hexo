---
title: Raspberry Pi node.js and how to start with programming GPIO (Pixpress project
  on Github) - Part 01
id: 718
categories:
  - Uncategorized
date: 2016-01-18 16:52:41
tags:
---

Last time I was a little bit busy... because of playing with Raspberry Pi :) Yeah... I think it made me motivated to digg deeper in nodejs/expressjs. 

Firstly what I needed to do was installation of system on SD card. Ive downloaded Raspbian ([here](https://www.raspberrypi.org/downloads/raspbian/)) and installed Jessie installation with Xwindows.([here](https://www.raspberrypi.org/documentation/installation/installing-images/) you can find info how to install it) It wasn't very stable because everytime when Ive installed node and VNC it just collapsed after simple reboot. Than I needed to reinstall it second time / third time / fourth time... I was frustrated and installed simple version of Raspbian - Lite. This version is more stable and since Ive installed it I didnt needed any reinstallation of system. And finally

## OS is stable!
What was next? Node.js installation! What you need is you need to connect to your raspberry through SSH. Open your terminal and write:

<pre class="line-numbers"><code class="language-javascript">ssh pi@&lt;IP_of_RaspberryPI&gt;</code></pre> 

You will be asked for password. What you need to write (till you change the admin password) is:

<pre class="line-numbers"><code class="language-javascript">raspberry</code></pre> 

And now you can start with installation on node.js

<pre class="line-numbers"><code class="language-javascript">sudo apt-get install node</code></pre> 

Than install NPM:

<pre class="line-numbers"><code class="language-javascript">sudo apt-get install npm</code></pre> 

Short version of installation is:

<pre class="line-numbers"><code class="language-javascript">sudo apt-get install node npm</code></pre> 

## Lets bring GPIO to life!
Lets create node project:

<pre class="line-numbers"><code class="language-javascript">npm init</code></pre> 

Than what you will need is install onoff library:

<pre class="line-numbers"><code class="language-javascript">npm i onoff --save</code></pre> 

This will help you to enable / disable GPIO pins. To see how PINs in RPi are numbered lets check this image:
[![gpiorpi2](http://fedojo.com/wp-content/uploads/2016/01/gpiorpi2.png)](http://fedojo.com/wp-content/uploads/2016/01/gpiorpi2.png)

As you can see it rahter has no logic order :) Lets bring it to life! Lets create a file on.js

<pre class="lang:default decode:true " >var GPIO = require('onoff').Gpio,
led = new GPIO(18, 'out'),

led.writeSync(1);</pre> 

Now run it:

<pre class="line-numbers"><code class="language-javascript">node on.js</code></pre> 

Easily when you want to disable the LED you just need to change a code and in place of 1 put 0 like this:
<pre class="line-numbers"><code class="language-javascript">var GPIO = require('onoff').Gpio,
led = new GPIO(18, 'out'),

led.writeSync(0);</code></pre> 

## Automatic restart of app
If you are working on one file in node.js and you dont want to restert node app each time when you are changing the code inside the file just install the supervisor:

<pre class="lang:default decode:true " >npm i supervisor -g</pre> 

Than you can start app with supervisor:

<pre class="line-numbers"><code class="language-javascript">supervisor app.js</code></pre> 

Ok so what can you do next? Lets create some light effect. Create new file and add this code:

<pre class="line-numbers"><code class="language-javascript">var GPIO = require('onoff').Gpio,
led04 = new GPIO(4, 'out'),
led05 = new GPIO(5, 'out'),
led06 = new GPIO(6, 'out'),
led07 = new GPIO(7, 'out'),
led08 = new GPIO(8, 'out');

var leds = [led04, led05, led06, led07, led08],
    counter = 0;

console.log(leds.length);
setInterval(function() {
  leds.forEach(function(currentValue) {
    currentValue.writeSync(0);
  });

  leds[counter].writeSync(1);
  counter++;

  if (counter &gt;= (leds.length)) counter = 0;
  console.log(counter);
}, 300);</code></pre> 

So what is going on now? fristly led04 will be enabled than 04 will be disabled and 05 will be enabled. Next step 05 disabled 06 enabled. Than 06 disabled 07 enabled. Than 07 disabled 08 enabled. Than 04 enabled 08 disabled. Lets begin in step 01 :) As you can see it on video:

<iframe width="420" height="315" src="https://www.youtube.com/embed/ULER9V59pHY" frameborder="0" allowfullscreen></iframe>

As you can see this is pretty nice blinking effect:) 
In next part I will try to share information how to include express to this project and start connecting with server from external devices.

You can see the full project on Github.
https://github.com/fedojo/pixpress
