---
id: 37
title: Segmentation Fault in NS2
date: 2012-06-24T12:27:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=37
permalink: /?p=37
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/06/segmentation-fault-in-ns2.html
dsq_thread_id:
  - "1768378556"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;">
  Hi Friends &#8230;<br /> My friend who are using NS2 specially Ad-Hoc Simulation they sometime got this problem<br /> &#8220;Segmentation Fault &#8221;</p> 
  
  <address>
    <span style="font-family: 'Courier New', Courier, monospace;">arun@Merom:~/myNS2/Assignment/Wireless$ ns wireless-tcp1.tcl </span><br /> <span style="font-family: 'Courier New', Courier, monospace;">num_nodes is set 8</span><br /> <span style="font-family: 'Courier New', Courier, monospace;">warning: Please use -channel as shown in tcl/ex/wireless-mitf.tcl</span><br /> <span style="font-family: 'Courier New', Courier, monospace;">INITIALIZE THE LIST xListHead</span><br /> <span style="font-family: 'Courier New', Courier, monospace;">Starting Simulation&#8230;Sir !!!!</span><br /> <span style="font-family: 'Courier New', Courier, monospace;">channel.cc:sendUp &#8211; Calc highestAntennaZ_ and distCST_</span><br /> <span style="font-family: 'Courier New', Courier, monospace;">highestAntennaZ_ = 1.5,  distCST_ = 550.0</span><br /> <span style="font-family: 'Courier New', Courier, monospace;">SORTING LISTS &#8230;DONE!</span><br /> <span style="font-family: 'Courier New', Courier, monospace;">Segmentation fault</span>
  </address>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
  </div>
  
  <div>
    <span style="font-family: inherit;">I have a solution for that please go through this post and you will be happy ..</span>
  </div>
  
  <div>
    <span style="font-family: inherit;"> </span>
  </div>
  
  <div>
    <span style="font-family: inherit;"> </span>
  </div>
  
  <div>
    <span style="font-family: inherit;">actually this segmentation fault problem happens due to &#8220;DSR&#8221; Ad-Hoc routing table  when we are using any type  of queue with DSR routing Algo . so CMU made a &#8220;</span><span style="background-color: white;">CMUPriQueue&#8221; to deal with that so please follow that code &#8230;..</span>
  </div>
  
  <div>
    <span style="background-color: white;"> </span>
  </div>
  
  <div>
    <span style="background-color: white;"> </span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;">if { $val(rp) == &#8220;DSR&#8221; } {</span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;">set val(ifq)            CMUPriQueue</span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;">} else {</span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;">set val(ifq)            Queue/DropTail/PriQueue</span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="background-color: white;">}</span><span style="background-color: white;"> </span></span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="background-color: white;"> </span></span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="background-color: white;"> </span></span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="background-color: white;"> </span></span>
  </div>
  
  <div>
    <span style="font-family: Arial, Helvetica, sans-serif;">so there will be no segmentation fault &#8230;.</span>
  </div>
  
  <div>
    <span style="font-family: Arial, Helvetica, sans-serif;">Enjoy please like it &#8230; if your problem is solved .</span>
  </div>
  
  <div>
    please paste this before creating GOD
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="background-color: white;"> </span></span>
  </div>
  
  <div>
    <span style="font-family: 'Courier New', Courier, monospace;"><span style="background-color: white;"> </span></span>
  </div>
</div>