---
title: >-
  Ionic - front end framework for mobile applications - prepare your
  environment.
tags:
  - android
  - cordova
  - ionic
  - ios
  - phonegap
id: 66
categories:
  - Android
  - iOS
  - Mobile aplications
  - PhoneGap / Cordova
  - Windows Phone
date: 2014-05-16 16:07:04
---

Have you been working with Angularjs? Do you need to create an mobile app based on this framework? IONIC is created for you.

<!--more-->

“The goal of what we’re trying to do is basically provide the most compelling alternative to building with the iOS or Android native SDKs and any other native SDKs that we end up supporting in the future,” Lynch says. He notes labor and cost savings with Web development as opposed to the native variety. “Instead of spending half a year on two entirely different code bases for iOS and Android, you can build just one with HTML5.”

&nbsp;

**Quick start**

1\. Firstly you will need to install ionic and phonegap (cordova) on your machine.
<pre style="color: #111111;">sudo npm install -g phonegap</pre>
&nbsp;

2\. Install XCode (App Store)

&nbsp;

3\. Install Android SDK (ADT [http://developer.android.com/sdk/index.html?hl=sk](http://developer.android.com/sdk/index.html?hl=sk "Download Android SDK"))

&nbsp;

4\. Download and Install ANT ([http://ant.apache.org/bindownload.cgi](http://ant.apache.org/bindownload.cgi "Download Apache Ant"))

&nbsp;

5\. Edit or create .bash_profile in your home directory
<pre class="lang:default decode:true">cd ~
touch .bash_profile
open -e .bash_profile
</pre>
&nbsp;

6\. Add ADT and ANT path into .bash_profile file
<pre class="lang:default dec   &lt;pre class=" lang:default="" decode:true="">export PATH=${PATH}:/Applications/adt/sdk/platform-tools/
export PATH=${PATH}:/Applications/adt/sdk/tools
export PATH=${PATH}:/Applications/ant/bin/
</pre>
Replace:
Applications/adt/sdk
Applications/ant

with your path to this folders

&nbsp;

7\. Install IONIC framework

    npm install -g cordova ionic

&nbsp;

8\. Start project and run the code
<pre class="lang:default decode:true">ionic start myApp tabs
cd myApp
ionic platform add ios
ionic platform add android

ionic build ios
ionic emulate ios</pre>
&nbsp;

9\. For testing in web browser with live reloader
<pre class="lang:default decode:true">ionic serve</pre>
&nbsp;
10\. Native test
- Android - you have to enable debug mode on your device and then plug it to your machine

<pre class="lang:default decode:true " >cordova run android</pre> 

- iOS - its not so simple as on Android devices but... you have to create a project in XCode from code in /platforms/ios

&nbsp;

[http://ionicframework.com/docs/guide/](http://ionicframework.com/docs/guide/ "Ionic framework guide")

[http://ionicframework.com/](http://ionicframework.com/ "IONIC Framework webpage")