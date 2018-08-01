---
id: 422
title: Link Aggregation LAG(IEEE 802.3ad)
date: 2014-06-12T00:26:34+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=422
permalink: /?p=422
dsq_thread_id:
  - "2760980617"
categories:
  - "Geek's Stuffs"
tags:
  - LAG
  - Linux
  - Networking
---
<p style="text-align: justify;">
  Yesterday my colleague asked me about LAG, whats the meaning of LAG and what&#8217;s the use of it?
</p>

<h2 style="text-align: justify;">
  What does Link Aggregation (LAG) mean?
</h2>

<p style="text-align: justify;">
  Link aggregation (LAG) is used to describe various methods for using multiple parallel network connections to increase throughput beyond the limit that one link (one connection) can achieve. For link aggregation, physical ports must reside on a single switch. Split Multi-Link Trunking (SMLT) and Routed-SMLT (RSMLT) remove this limitation and physical ports are allowed to connect/split between two switches. This term is also known as Multi-Link Trunking (MLT), Link Bundling, Ethernet/Network/NIC Bonding or NIC teaming.
</p>

## Link Aggregation (LAG) :

<p style="text-align: justify;">
  Link aggregation is a technique used in a high-speed-backbone network to enable the fast and inexpensive transmission of bulk data. The best feature of link aggregation is its ability to enhance or increase the network capacity while maintaining a fast transmission speed and not changing any hardware devices, thus reducing cost. Cost Effectiveness LAG is a very common technique for establishing a new network infrastructure using extra cabling above the current requirements. Labor cost is much more than the cost of cabling. Thus, when a network extension is required, the extra cables are used without incurring any additional labor. However, this can be done only when extra ports are available. Higher-Link Availability This is the best feature of LAG. A communication system keeps working even when a link fails. In such situations, link capacity is reduced but data flow is not interrupted. Network Backbone Formerly, there were many techniques used for networking, but IEEE standards are always preferred. LAG supports network load balancing. Different load balancing algorithms are set by network engineers or administrators. Furthermore, network speed is increased by small increments, saving both resources and cost. Limitations With all kinds of implementations, each link and piece of hardware is standardized and engineered to not affect the network efficiency or link speed. Additionally, with single-switching all kind of ports (802.3ad, broadcast, etc.) must reside on a single switch or the same logical switch.
</p>

<p style="text-align: justify;">
  <a href="http://www.freebsd.org/doc/handbook/network-aggregation.html" target="_blank">How to setup LAG in linux BOX</a>
</p>

<p style="text-align: justify;">
  Thanx to <a href="http://www.techopedia.com/definition/24969/link-aggregation-lag" target="_blank">Techopedia</a>
</p>