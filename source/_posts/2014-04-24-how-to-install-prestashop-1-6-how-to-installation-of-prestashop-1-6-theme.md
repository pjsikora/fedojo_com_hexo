---
title: How to install PrestaShop 1.6 / How to installation of PrestaShop 1.6 theme
tags:
  - cms
  - prestashop
id: 94
categories:
  - CMS
  - PrestaShop
date: 2014-04-24 20:38:08
---

Sometimes as a Front End Developer you will need to create a prestashop theme. You will need Prestashop installation so... Lets prepare it

&nbsp;

**What you will need?**

1.  Server (FTP/SFTP) login/password/host
2.  MySQL database login/password/dbname/host
&nbsp;

**Installation**

1.  Copy file to your server.
2.  Change write permisions for folders
<pre class="lang:default decode:true ">~/config/
~/cache/
~/log/
~/img/
~/mails/
~/modules/
~/themes/default-bootstrap/lang/
~/themes/default-bootstrap/pdf/lang/
~/themes/default-bootstrap/cache/
~/translations/
~/upload/
~/download/</pre>
&nbsp;
3.  Run installation process (write URL in browser)
&nbsp;

**After Installation process**

1.  Remove install folder
2.  Change admin folder name to for example folder123
&nbsp;

**Access Back-end of prestashop**
<pre class="lang:default decode:true">http://yoururl/admin123</pre>
admin123 is your choosed folder name for admin folder.

&nbsp;

**Intallation of PrestaShop theme**

1.  Copy needed modules to modules dir
2.  Copy theme to themes dir
3.  Open prestashop BE
4.  Preferences &gt; Themes  and choose your new theme.
5.  Sometimes in new theme you will need to regenerate your thumbnails. Regenerate them and...
&nbsp;

&nbsp;

Thats it!