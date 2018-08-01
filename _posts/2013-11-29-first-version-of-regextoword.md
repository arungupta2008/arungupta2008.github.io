---
id: 235
title: First Version of RegextoWord
date: 2013-11-29T12:48:48+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=235
permalink: /?p=235
dsq_thread_id:
  - "2009292112"
categories:
  - "Geek's Stuffs"
  - Perl
tags:
  - Coding
  - Project
  - RegextoWord
---
Hello Guys. I have been working in Perl from last 5 moths and while writing Regular Expressions i face difficulty to understand or write the Regular expressions. Well now it&#8217;s ok, but i thought can we covert the RegEx to understandable language.
  
So i started an <a href="https://github.com/arungupta2008/RegextoWord/blob/b0c441c5a414c4a61faa95d1307f876b6f7ac2e6/RegextoString.c" title="project" target="_blank">project</a>, here is the first version of the RegExtowordV1.0. 

It can accept(Parse) Strings like 

<pre>^arun
^[arun]
^[a-z]
^[A-Z]
^[a-zA-Z0-9]
^[a-zA-Z0-9]Arun
^[a-zA-Z0-9]A\^\%run
[arun]
(A|R|U|N)
</pre>

Basically in first version it can parse string (any word , digit special character, ^ ,[] () ).
  
please do give some feedback about it.