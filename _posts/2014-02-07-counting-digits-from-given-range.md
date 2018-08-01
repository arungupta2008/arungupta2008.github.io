---
id: 266
title: Counting Digits from given Range
date: 2014-02-07T12:58:41+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=266
permalink: /?p=266
dsq_thread_id:
  - "2232463353"
categories:
  - Algorithm
  - C or C++
  - "Geek's Stuffs"
tags:
  - Algorithm
  - Coding
  - Technical
---
Imagine you sell those metallic digits used to number houses, locker doors, hotel rooms, etc. You need to find how many of each digit to ship when your customer needs to number doors/houses:
  
1 to 100
  
51 to 300
  
1 to 2,000 with zeros to the left
  
The obvious solution is to do a loop from the first to the last number, convert the counter to a string with or without zeros to the left, extract each digit and use it as an index to increment an array of 10 integers.
  
I wonder if there is a better way to solve this, without having to loop through the entire integers range.
  
<a href="https://github.com/arungupta2008/digitcount" target="_blank">GitHub Link</a>
  
Thanx to mathematician&#8217;s [Post](http://www.artofproblemsolving.com/Forum/viewtopic.php?p=1741600#1741600) that helped me to understand the complexity of problem, i just understood the equation and converted it to code. Enjoy !