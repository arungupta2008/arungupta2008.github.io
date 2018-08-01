---
id: 296
title: Regex to validate the Email
date: 2014-03-07T15:51:13+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=296
permalink: /?p=296
dsq_thread_id:
  - "2379368096"
categories:
  - "Geek's Stuffs"
  - Linux
  - Perl
tags:
  - Coding
  - Email
  - Perl
---
Here i am sharing a regex to validate the Email.

This is an standard version of regex.

<pre>^([a-zA-Z0-9\!\#\$\%\&\'\*\+\/\=\?\^\_\`\{\|\}\~\-]+)(?:\.[A-Za-z0-9\!\#\$\%\&\'\*\+\/\=\?\^\_\`\{\|\}\~\-]+)*@([a-zA-Z0-9]([\-]?[a-zA-Z0-9]+)*\.)+([a-zA-Z0-9]{0,6})\$</pre>

It can validate email like

Valid Emails

<pre>arungupta@gmail.com
arun+gupta+ramjiki+@gmail.com
a.little.lengthy.but.fine@dept.example.com
disposable.style.email.with+symbol@example.com
other.email-with-dash@example.com
arun@daiict.ac.in
arun_gupta@gmail.com</pre>

Invalid Emails

<pre>me@
@example.com
me.@example.com
.me@example.com
me@example..com
me.example@com
me\@example.com</pre>