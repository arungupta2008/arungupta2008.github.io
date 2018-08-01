---
id: 98
title: How to recover your blog password
date: 2013-03-21T17:48:41+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=98
permalink: /?p=98
dsq_thread_id:
  - "2613176503"
categories:
  - "Geek's Stuffs"
  - Uncategorized
tags:
  - Blog
  - Password
---
Hello , Friends

i have a website which is hosted be wordpress  , i updated my wordpress from 3.5 to newer version but from that time i was not able to access the my wp-admin menu .

i googled a little bit then i didn&#8217;t get any thing then  i tricked with my website &#8230;&#8230;

1. i downloaded everything from my hosting place to my computer through filezila

2. the i made some changes in files ** &#8220;admin.functions.php&#8221; **in &#8220;upgrade-functions.php&#8221;  .

changes was i added

<pre>wp_set_password('password',1);</pre>

Put in your own new password for the main admin user. The &#8220;1&#8221; is the user ID number in the wp_users table.

3. Upload the modified file back to your site.

4. After you then are able to login, make sure to go back and remove that code. It will reset your password on every page load until you do.

&nbsp;

Cheers !!!

&nbsp;