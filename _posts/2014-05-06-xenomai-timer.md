---
id: 382
title: Xenomai Timer
date: 2014-05-06T12:45:11+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=382
permalink: /?p=382
dsq_thread_id:
  - "2664262766"
categories:
  - C or C++
  - "Geek's Stuffs"
  - Linux
  - Uncategorized
tags:
  - Coding
  - Timer
  - Xenomai
---
<p style="text-align: justify;">
  Xenomai Timer :Xenomai has two time sources: the sytem timer, which counts the number of nanoseconds since 1970, and a hardware dependent high resolution counter which counts the time since an unspecified point in time (usually the system boot time). This hardware dependent high resolution counter is called &#8220;tsc&#8221; on a PC, and gave its name to Xenomai native API calls.rt_timer_tsc returns the value of this hardware dependent high-resolution counter.<br /> rt_timer_info returns the same thing in the tsc member of the RT_TIMER_INFO structure, and the value of the system timer at exactly the same time as when the high-resolution counter was read.
</p>

<p style="text-align: justify;">
  This allows to have a correspondence between the two time sources.
</p>

<p style="text-align: justify;">
  rt_alarm_inquire is not related to this and returns some information<br /> about a given alarm. Now, if you allow me, a little advice for the implementation of a &#8220;timer library&#8221;: you could be tempted to create only one periodic alarm object with Xenomai, and to manage a timer list yourself. Don&#8217;t do this. Creating an alarm object for each timer library object make Xenomai aware of the existence of all your application timers, this has several
</p>

<p style="text-align: justify;">
  advantages:<br /> &#8211; it gives you information about all your timers in /proc/xenomai<br /> &#8211; it allows Xenomai to use its anticipation algorithm for all your timers<br /> &#8211; if you are concerned about the scalability of Xenomai timers list<br /> management, you can check the options in the &#8220;Scalability&#8221; menu of<br /> Xenomai configuration menu (&#8220;Real-time subsystem&#8221; sub-menu of kernel<br /> configuration menu).<br /> more about timers
</p>

<p style="text-align: justify;">
  Xenomai POSIX skin supports two clocks:<br /> CLOCK_REALTIME maps to the nucleus system clock, keeping time as the amount of time since the Epoch, with a resolution of one system clock tick.
</p>

<p style="text-align: justify;">
  CLOCK_MONOTONIC maps to an architecture-dependent high resolution counter, so is suitable for measuring short time intervals. However, when used for sleeping (with <a title="Sleep some amount of time." href="http://www.xenomai.org/documentation/trunk/html/api/group__posix__time.html#ga924d51d78cdcd9d7dee2613fb3a33cd1">clock_nanosleep()</a>), the CLOCK_MONOTONIC clock has a resolution of one system clock tick, like the CLOCK_REALTIME clock.<a href="http://www.xenomai.org/documentation/trunk/html/api/group__posix__time.html" target="_blank">[1]</a>
</p>