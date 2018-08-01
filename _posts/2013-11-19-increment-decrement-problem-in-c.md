---
id: 230
title: 'Increment decrement  problem in c'
date: 2013-11-19T18:26:22+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=230
permalink: /?p=230
dsq_thread_id:
  - "1979122906"
categories:
  - C or C++
  - "Geek's Stuffs"
tags:
  - C-Skills
  - Coding
---
<pre>Hello guys let's we have an syntax and related values let's see how this works. Evaluate the given syntax 
z = ++x + y-- - ++y - x-- - x-- - ++y - x--
where x = 7 y = -3</pre>

<pre>z = ((((((++x + y--) - ++y) - x--) - x--) - ++y) - x--)
so first(++x + y--) will be evaluated
 (++x + y--)
   8 + (-3)        x=8 y = -4
 z = (((((5 - ++y) - x--) - x--) - ++y) - x--)
 (5 - ++y)
  5 - ( -3)  x=8 y = -3

 z = ((((8 - x--) - x--) - ++y) - x--)
 (8 - x--)
  8 - 8      x =7 y = -3 
 z = (((0- x--) - ++y) - x--)
 (0- x--)
  0 - 7      x =6 y = -3
 z = (((-7 - ++y) - x--)
 (-7 - ++y)
  -7 - (-2)  x = 6 y = -2
 z = (-5 - x--)
 -5 -6       x =5 y -2
 z = -11</pre>

So answer is -11