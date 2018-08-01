---
id: 272
title: Vmware Problem with ubuntu 13.10
date: 2014-02-08T14:31:23+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=272
permalink: /?p=272
dsq_thread_id:
  - "2237160530"
categories:
  - "Geek's Stuffs"
  - Linux
tags:
  - Linux
  - Ubuntu
  - VmWare
---
<p style="text-align: justify;">
  I installed Vmware it was working well, i updated/upgraded OS firmware, now it&#8217;s not working. i googled it and found the solution. before telling the solution i wanna tell why this is coming.
</p>

<p style="text-align: justify;">
  VMware Player has a nice auto-detection of kernel changes, and requests the user to compile the required modules in order to load them. This happens from time to time after a regular update of your system. Usually, the dialog of VMware Kernel Module Updater pops up, asks for root access authentication, and completes the compilation.
</p>

<p style="text-align: justify;">
  In theory this is supposed to work flawlessly but in reality there are pitfalls occassionally. With the recent upgrade to Ubuntu 13.04 Raring Ringtail and the latest kernel 3.8.0-21 the actual VMware Kernel Module Updater simply disappeared and the application wouldn&#8217;t start as expected. When you launch VMware Player as super user (root) the dialog would stall.
</p>

Solution is :

<pre>sudo vmware-modconfig --console --install-all</pre>

This solution worked for me.

<pre>My machine was VMware Player 5.0.2 build-1031769</pre>