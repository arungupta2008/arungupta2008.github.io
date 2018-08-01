---
id: 38
title: Adding A new Protocol in ns 2.35
date: 2012-06-03T18:59:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=38
permalink: /?p=38
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/06/adding-new-protocol-in-ns-235.html
dsq_thread_id:
  - "1768378452"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  Just Remember from my last post that is for ns .2.34<br />but i am also updating a patch that when you are adding protocol on ns2.35<br />in packet header you please add at<br />last</p> 
  
  <p>
    <span style="color: #cc0000;"><br /></span>
  </p>
  
  <p>
    <span style="color: #cc0000;">// WFRP packet</span><br /><span style="color: #cc0000;">static const packet_t PT_WFRP = 73;</span><br /><span style="white-space: pre;"><span style="color: #cc0000;"> </span></span><br /><span style="color: #cc0000;">        // insert new packet types here</span><br /><span style="color: #cc0000;">static packet_t  PT_NTYPE = 74; // This MUST be the LAST one</span><br /><span style="color: #cc0000;"><br /></span><br /><span style="color: #cc0000;"><br /></span><br />so this protocol will work.
  </p>
  
  <p>
    as in my last post please put on line
  </p>
  
  <p>
    272 in packet.h
  </p>
  
  <p>
    <span style="background-color: #f8f8f8; color: #373737; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace; font-size: 16px; line-height: 16px;">type == PT_WFRP ||</span>
  </p>
  
  <p>
    and<br /><code style="background-image: none !important; border: 0px !important; bottom: auto !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">name_[PT_WFRP] = </code><code style="background-image: none !important; border: 0px !important; bottom: auto !important; color: blue !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">"WFRP"</code><code style="background-image: none !important; border: 0px !important; bottom: auto !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">;</code>
  </p>
  
  <p>
    in line 424<br />note : this above line should be above on this line<br />name_[PT_NTYPE]= &#8220;undefined&#8221;;
  </p>
  
  <p>
    next changes in <span style="background-color: #fcfcfc; color: #373737; font-family: Arial, sans-serif; font-size: 16px; line-height: 23px; text-align: -webkit-auto;"> </span><span style="background-color: #fcfcfc; color: #373737; font-family: Arial, sans-serif; font-size: 16px; line-height: 23px; text-align: -webkit-auto;">cmu-trace.h and cmu-trace.cc. files</span><br />at trace/cmu-trace.h<br />at line 163 add<br /><code style="background-image: none !important; border: 0px !important; bottom: auto !important; color: rgb(0, 102, 153) !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; font-weight: bold !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">void</code>    <code style="background-image: none !important; border: 0px !important; bottom: auto !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">format_wfrp(Packet *p, </code><code style="background-image: none !important; border: 0px !important; bottom: auto !important; color: rgb(128, 128, 128) !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; font-weight: bold !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">int</code> <code style="background-image: none !important; border: 0px !important; bottom: auto !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">offset);</code><br /><code style="background-image: none !important; border: 0px !important; bottom: auto !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">.......................................</code><br /><code style="background-image: none !important; border: 0px !important; bottom: auto !important; direction: ltr !important; display: inline !important; float: none !important; font-family: Consolas, 'Bitstream Vera Sans Mono', 'Courier New', Courier, monospace !important; font-size: 1em !important; height: auto !important; left: auto !important; line-height: 1.1em !important; margin: 0px !important; outline: 0px !important; padding: 0px !important; position: static !important; right: auto !important; top: auto !important; vertical-align: baseline !important; width: auto !important;">and other things are added on that post (last)</code>
  </p>
  
  <p>
    </div>