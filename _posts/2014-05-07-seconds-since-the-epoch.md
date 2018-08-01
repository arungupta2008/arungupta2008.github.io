---
id: 387
title: 'Seconds Since the &#8220;Epoch&#8221;'
date: 2014-05-07T16:27:23+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=387
permalink: /?p=387
dsq_thread_id:
  - "2667185454"
categories:
  - "Geek's Stuffs"
tags:
  - C
  - Coding
  - Epoch
  - Timer
---
<p style="text-align: justify;">
  I was supposed to write a RT (Real Time) logging which doesn&#8217;t call a single Linux CALL.<br /> I had only seconds from 1st Jan 1970 (Called Eposh).
</p>

<p style="text-align: justify;">
  A value that approximates the number of seconds that have elapsed since the Epoch. A Coordinated Universal Time name (specified in terms of seconds (<i>tm_sec</i>), minutes (<i>tm_min</i>), hours (<i>tm_hour</i>), days since January 1 of the year (<i>tm_yday</i>), and calendar year minus 1900 (<i>tm_year</i>)) is related to a time represented as seconds since the Epoch, according to the expression below.
</p>

<p style="text-align: justify;">
  If the year is <1970 or the value is negative, the relationship is undefined. If the year is>=1970 and the value is non-negative, the value is related to a Coordinated Universal Time name according to the C-language expression, where <i>tm_sec</i>,  <i>tm_min</i>,  <i>tm_hour</i>,  <i>tm_yday</i>,  and  <i>tm_year</i> are all integer types:
</p>

> <pre><i>tm_sec</i> <tt>+</tt> <i>tm_min</i><tt>*60 +</tt> <i>tm_hour</i><tt>*3600 +</tt> <i>tm_yday</i><tt>*86400 +
    (</tt><i>tm_year</i><tt>-70)*31536000 + ((</tt><i>tm_year</i><tt>-69)/4)*86400 -
    ((</tt><i>tm_year</i><tt>-1)/100)*86400 + ((</tt><i>tm_year</i><tt>+299)/400)*86400
</tt></pre>

<p style="text-align: justify;">
  The relationship between the actual time of day and the current value for seconds since the Epoch is unspecified.
</p>

<p style="text-align: justify;">
  How any changes to the value of seconds since the Epoch are made to align to a desired relationship with the current actual time is implementation-defined. As represented in seconds since the Epoch, each and every day shall be accounted for by exactly 86400 seconds.
</p>

**Note:**
:   The last three terms of the expression add in a day for each year that follows a leap year starting with the first leap year since the Epoch. The first term adds a day every 4 years starting in 1973, the second subtracts a day back out every 100 years starting in 2001, and the third adds a day back in every 400 years starting in 2001. The divisions in the formula are integer divisions; that is, the remainder is discarded leaving only the integer quotient.

You can convert epoch Seconds to current time please look at this <a href="https://github.com/arungupta2008/code/blob/master/Epoch_to_date.c" target="_blank">LINK</a>.