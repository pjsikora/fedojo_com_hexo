---
title: Localtunnel and NGRok.io - how to show your localhost to client
id: 657
categories:
  - Software
date: 2015-06-11 12:54:56
tags:
---

Have you ever had a problem with showing your localhost to other person? For example you dont want to send full project to your hosting and you just want to show a one view and ask a client for something. Or you want to talk with designer about some issues but as I described it before you dont want to upload full project on server?

Here comes LocalTunnel and ngrok.io.

I was using LocalTunnel for about one year. Its really easy to install and use but... yes there is a but... It disconnects sometimes without any reason. And you loose your long URL which you need to retype in your address input. On desktop its not going to be a problem because you have a fast fingers but on iPad and or any mobile device its rather making me nervous.

Ngrok.io is more stable and thats why I recommend this tool.

1.  Firstly you will need to download your binary files from [ngrok.io](https://ngrok.com/)
2.  Than run your localhost with your PHP/Node.js/Ruby server
3.  go to command line and run ngrok on http protocol with port chosen port (Im using port 80 but you can choose your own): ngrok http 80
Thats it! Voila!

If you want to share your virtual host:

<pre class="lang:default decode:true " >ngrok http -host-header=your.host 80</pre> 

PS. Thanks **Anna Migas **for your tip! :)