---
id: 177
title: connecting to archive.ubuntu.com takes too long
date: 2013-09-26T15:08:28+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/?p=177
permalink: /?p=177
dsq_thread_id:
  - "1798453671"
categories:
  - Linux
  - Uncategorized
tags:
  - BUG
  - Linux
  - Ubuntu
---
I have a Ubuntu 13.04 that I just installed fresh. Now if I try to do anything with `apt-get`, it tries to connect to `archive.ubuntu.com` .. It stays at `[Connecting to archive.ubuntu.com (2001:67c:1360:8c01::1a)]` phase for like 2 minutes, after which it actually starts to communicate and download stuff &#8230;

Eventually it always connects, but in waits at the `[Connecting to archive.ubuntu.com (2001:67c:1360:8c01::1a)]` phase everytime for like 2 minutes !

I didn&#8217;t have this problem previously on Ubuntu 13.04, right after reinstalling the OS ..

## Solution:

I figured out the problem. Posted below as an answer!

Running the following command in Terminal tells if IPv6 is enabled or not:

`cat /proc/sys/net/ipv6/conf/all/disable_ipv6`

`` means its enabled, while `1` means its disabled.

To disable IPv6 from within Terminal, enter the following and reboot:

    echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
    echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
    echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
    echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
    

After boot, re-run the first command, and it should be `1` now, after running this run

sudo sysctl -p

all output should be 1, now ipv6 is disable here.