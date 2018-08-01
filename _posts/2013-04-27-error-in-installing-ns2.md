---
id: 111
title: Error in installing NS2
date: 2013-04-27T17:26:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=111
permalink: /?p=111
dsq_thread_id:
  - "1772943899"
categories:
  - NS2
tags:
  - Coding
  - ns2
---
Hello ,

errors while installing ns2

> <span style="color: #808000;">can&#8217;t find X includesotcl-1.13 configuration failed! Exiting &#8230;Please check http://www.isi.edu/nsnam/ns/ns-problems.html</span>

solutions for that :

please copy and paste in shell

<pre>sudo apt-get install xorg-dev
sudo apt-get install libx11-dev
sudo apt-get install libxt-dev

Enjoy :)

</pre>