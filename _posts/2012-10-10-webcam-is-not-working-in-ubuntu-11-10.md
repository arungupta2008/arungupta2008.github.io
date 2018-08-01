---
id: 19
title: Webcam is not Working in Ubuntu 11.10
date: 2012-10-10T08:03:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=19
permalink: /?p=19
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/10/webcam-is-not-working-in-ubuntu-1110.html
categories:
  - Uncategorized
tags:
  - Linux
  - Ubuntu
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  Hi Guys back with some new stuffs of Linux ..<br />this happens frequently in Ubuntu, after some of using the Ubuntu webcam does not works.<br />so i have solution here .<br />it was taken long time to me found out the solution .<br />this solution worked in my laptop .</p> 
  
  <p>
    <span style="background-color: #f7f6f5; font-size: 13px;"><span style="font-family: Courier New, Courier, monospace;">sudo apt-get install v4l2ucp</span></span><br /><span style="font-family: Courier New, Courier, monospace;"><span style="background-color: #f7f6f5; font-size: 13px;">sudo v4l2ucp</span><span style="background-color: #f7f6f5; font-size: 13px;"> </span></span>
  </p>
  
  <p>
    then run<br /><span style="font-family: Courier New, Courier, monospace;">cheese </span>
  </p>
  
  <p>
    it will work   
  </p>
</div>