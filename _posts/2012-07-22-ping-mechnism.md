---
id: 29
title: Ping Mechnism
date: 2012-07-22T18:06:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=29
permalink: /?p=29
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/07/ping-mechnism.html
dsq_thread_id:
  - "1795631262"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  </p> 
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">PING</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Everybody knows that the ping utility is used to check network connectivity between two hosts, but what happens when a user issues a ping? This article is designed to explain the basics of what happens on a network when a ping is issued. Imagine the following scenario;</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">You have PC-A in subnet 192.168.1.0/24, PC-B in subnet 192.168.2.0/24 and a router connected to both subnets. You need to check if PC-A can connect to PC-B.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">For the purposes of this article we will use the following IP addresses and MAC addresses;</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">PC-A </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">192.168.1.10<span style="white-space: pre;"> </span>MAC Address<span style="white-space: pre;"> </span>00:00:00:00:00:10<span style="white-space: pre;"> </span></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Default Gateway<span style="white-space: pre;"> </span>192.168.1.15</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Router Interface E0 </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">192.168.1.15 MAC Address<span style="white-space: pre;"> </span>00:00:00:00:00:15</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Router Interface E1 </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">192.168.2.20<span style="white-space: pre;"> </span>MAC Address<span style="white-space: pre;"> </span>00:00:00:00:00:20</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">PC-B </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">192.168.2.25<span style="white-space: pre;"> </span>MAC Address<span style="white-space: pre;"> </span>00:00:00:00:00:25</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Default Gateway<span style="white-space: pre;"> </span>192.168.2.20</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">A user on PC-A types in “ping 192.168.2.25”</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">The first thing to happen is that ICMP (Internet Control Management Protocol) creates data. This is just the alphabet. IP (Internet Protocol) on PC-A creates a packet containing the Destination IP Address (192.168.2.25), the Source IP Address (192.168.1.10), the data, and a protocol field. The protocol field informs the receiving host where to pass the data to, in this example the protocol field would be set to 0x1h to indicate ICMP. (0x indicates that the following is an hexadecimal number)</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Once the packet has been created ARP (Address Resolution Protocol) is then used to identify the MAC (Media Access Control / Hardware address / Burned Address) address of the destination host. This can happen in a number of ways, the first to happen is that ARP checks it’s cache to see if it has a match to the Destination IP Address. If not then ARP sends out an ARP broadcast to the Ethernet MAC broadcast address (FF:FF:FF:FF:FF:FF)</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">“Who has 192.168.2.25? Please tell 000000000010”</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">You will notice that PC-A is asking for replies to be sent to the MAC address. This is because computers communicate only with MAC addresses on LANs (Local Area Networks)</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">If no response is received by PC-A, then ARP & IP assume that 192.168.2.25 is on a remote subnet and therefore would require routing. At this point the IP address and the MAC address of the default gateway is required. In a Windows machine the registry is consulted in order to get the IP address of the default gateway (192.168.1.15). ARP then consults it’s cache to see if it has match to the IP address of the default gateway, if not then another ARP broadcast is sent</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">“Who has 192.168.1.15? Please tell 000000000010”</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Because this is a broadcast ALL hosts on the 192.168.1.0/24 subnet will receive this frame. The router interface E0 will read the frame and identify itself as the interface with the requested IP address. The router will then reply;</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">“I have 192.168.1.15. MAC address is 000000000015”</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">As the request asked for a reply direct to PC-A the frame sent from the router will be directed towards PC-A and not sent as a broadcast. The router will also cache the MAC address of PC-A, which it received via the broadcast sent by ARP to locate the MAC address of the router.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Once IP at PC-A as received the message from the router interface it will pass the packet created earlier and the MAC Destination address down to the Data Link Layer. </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">The Data Link Layer creates a frame containing the Destination MAC address, the Source MAC address, A FCS (Frame Check Sequence, used to verify the data has not been corrupted) and an Ether_Type field, in this example the field will be set to 0x8 to indicate IP. This Frame encapsulates the packet passed down from IP at the Network Layer. The MAC address of the router is also cached into the ARP cache on PC-A</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Once the frame has been created it is passed down to the Physical Layer where the frame is placed onto the wire one bit at a time. Every host on subnet 192.168.1.0/24 will receive this frame, build it, and check the Destination MAC address, if it is not a match the frame is discarded. At the router interface, E0, the Destination MAC address is a match. The router then checks the Ether_Type field (0x8 = IP) pulls the packet from the frame, discards the frame and passes the packet up to IP at the Network Layer. </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">At the Network Layer the Destination IP address is checked to see if it is a match, in this example the Destination IP address is 192.168.2.25, however the IP address of the router interface which received the frame is 192.168.1.15, and is not a match. The router then consults it’s routing table for the destination IP network address (192.168.2.0). If there is no match in the routing table the packet is discarded and a “Destination Network unavailable” message is returned to PC-A</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">If there is a match in the routing table then the router will switch the packet to the interface configured to send information to the destination IP Network Address, in this example E1.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Interface E1 now needs to know the MAC address of the machine with IP address 192.168.2.25. The first thing it does is check the ARP cache, no match in the cache, E1 then send out an ARP broadcast.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">“Who has 192.168.2.25? Please tell 000000000020”</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Because PC-B is on the same subnet as E1, PC-B responds</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">“I have 192.168.2.25. MAC address is 0000000025”</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">IP at Interface E1, on the router, then passes the packet (created at PC-A) and the Destination MAC address for 192.168.2.25 down to the Data Link Layer. The Data Link Layer then creates a frame containing the Destination MAC address, Source MAC address, FCS and an Ether_Type field (again set to 0x1h to indicate IP), which encapsulates the IP packet. </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">(The MAC address of PC-B is placed into the ARP cache on Interface E1, and the MAC address of interface E1 is placed into the cache of PC-B)</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">The frame is then passed down to the Physical Layer to be placed on the wire one bit at a time. Again all hosts on the 192.168.2.0/24 subnet will receive the frame, build it, check it, discard it with the exception of PC-B which will match the Destination MAC address. PC-B will then check the Ether_Type field, pull the packet from the frame, discard the frame and pass the packet to the protocol indicated in the Ether_Type field, in this example IP. </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">IP then checks the Destination IP address in the packet and finds a match. It will then check the Protocol field (0x1h = ICMP) and pass the data to ICMP. ICMP recognises that the data sent is an echo request, and will then create an echo response message.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">The echo response is then passed to IP, which will then build a packet, consisting of the Destination IP address (192.168.1.10), the Source IP address (192.168.2.25) the data from ICMP, and the protocol field. Once the packet is built the MAC address of the IP address 192.168.1.10 is required. ARP checks it’s cache, if there is no match an ARP broadcast is sent.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">“Who has 192.168.1.10? Please tell 000000000025”</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Because 192.168.1.10 is on a remote subnet, and routers do not pass broadcasts there is no response. </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">The default gateway is then required for PC-B. The default gateway is configured as 192.168.2.20 and the ARP cache is checked. As PC-B cached the MAC address of interface E1, a match is found and there is no need to send out an ARP broadcast.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">Now that the MAC address of the default gateway has been resolved the packet and the Destination MAC address is then passed down to the Data Link Layer.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">At the Data Link Layer a frame is built which consists of the Destination MAC address, the Source MAC address, the FCS and the Ether_Type field (again set to 0x8 to indicate IP). The frame encapsulates the packet passed down from IP. The complete frame is then passed down to the Physical Layer to be put onto the wire one bit at a time.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">At Interface E1 of the router, the frame is received, the Destination MAC address is then checked and found to be a match. The Ether_Type field is then checked, the packed is pulled from the frame, the frame is discarded and the packed passed to IP, as indicated in the Ether_Type field.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">IP on E1 checks the IP destination address and finds it is not a match. It then consults the routing table for the IP Network Address (192.168.1.0/24), if a match is found the packet is switched to the Interface configured for the 192.168.1.0/24 network, in this example E0.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">If no match is found then the packet is discarded. PC-A will receive a time-out error in this case, as the time set to receive replies has been exceeded. A destination network unavailable message is NOT sent to PC-A. If the message could be sent to PC-A then the router would obviously have a route to PC-A’s network and then would not need to generate the message!!</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">On Interface E0, the interface configured for 192.168.1.0/24, IP and ARP will then locate the MAC address for the IP address 192.168.1.10. ARP checks the cache, because the MAC address for PC-A was cached on the outgoing trip, there is a match and the packet and frame are then passed down to the Data Link Layer. </span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">The Data Link Layer will then build a frame, consisting of the Destination MAC address, the Source MAC address, Ether_Type field and the FCS. This frame encapsulates the packet passed down from IP and then passes the frame down to the Physical Layer to be placed onto the wire, one bit at a time.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">PC-A receives the frame sent from interface E0 on the router, checks the MAC address, finds a match, reads the Ether_Type field, pulls the packet from the frame, discards the frame and passes the packet to IP as indicated in the Ether_Type field. IP checks the Destination IP address and finds a match. IP will then read the Protocol field (0x1h = ICMP) and passes the data to ICMP.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">ICMP recognises the data as an echo response, ICMP acknowledges receipt by sending information to the user interface, (“!” with Cisco routers, “Reply from 192.168.2.25…….” and additional information in Windows), and then builds another echo request and the whole process begins again.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">The above is designed to give an overview of what happens on the network when data is sent from one machine to another. This is by no way to be considered complete as there are additional parameters which can be configured and created both within the IP packet and the Data-Link Frame. The above assumes the use of Ethernet_II frames on the network. No matter how big the network or how many routers the data passes through the process is identical to the above.</span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;"><br /></span></span>
  </div>
  
  <div style="text-align: -webkit-auto;">
    <span style="font-family: verdana, geneva, lucida, 'lucida grande', arial, helvetica, sans-serif;"><span style="font-size: 14px;">“variable_node”</span></span>
  </div>
</div>