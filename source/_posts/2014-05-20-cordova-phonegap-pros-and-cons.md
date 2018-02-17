---
title: Cordova / PhoneGap - pros and cons
tags:
  - android
  - cordova
  - ios
  - phonegap
  - windows phone
id: 41
categories:
  - Android
  - iOS
  - Mobile aplications
  - PhoneGap / Cordova
  - Windows Phone
date: 2014-05-20 14:22:42
---

There is an option to build mobile application without knowledge about native languages used on devices (Objective C or Java). In this case you just need to use PhoneGap/Cordova or for example Titanium.

## Why Cordova.js / Phonegap is it good aproach
In some cases you have a team with deep javascript knowledge but without knowledge about native languages (objective c, java) and you need to create a product for mobile devices. Of course the best aproach could be to write one code and compile it on both mobile systems (android, IOS). You are starting digging about some technology which will match to your team and... PhoneGap looks like the best technology at the horizon. And for sure it is with current assumptions ( one code for Android / iOS / Windows Phone, usage of Front End developers skills).

Some projects needs to be finished really fast or your at at the begining because you want to show MVP (minimal valuable project) which needs to be done in really short time. For front end developer its easy to develop code which can be compiled with cordova.

## Cordova.js / Phonegap covers enormous spectrum of devices
When you are trying to write code for both types of devices there can ocure some problems caused by specific behaviour of system. Debuging on IOS is suported by Safari because you can use its programming tools. Even if you compile app in xcode and run on iphone/ipad safari still recognize it as website. On Android its rather hard to deal with inspecting - you cannot use a tool similar to firebug. Debuging is based on stacktracing and good ecperience of developer.

## Cordova.js / Phonegap gives you access to native functionalities from Javascript level
Mobile apps based on SOAP webservices can be fully suported by modern javascript libraries and frameworks like angular.js, jquery, backbone.js etc. What if we need some other custom functions? You need to create a library in native language and use it from javascript. So still you have to got more knowledge about native languages.

## Summary
Pros:
- you can use your front end skills
- one code for Android / iOS / Windows Phone
- you can build a part of your app using webbrowser

Cons:
- big spectrum of devices (in case you wan to build an app for IOS and android at once)
- some of functionalities has to be build in native language
