---
id: 201
title: What would be the output of this Code ?
date: 2013-10-31T10:10:10+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=201
permalink: /?p=201
dsq_thread_id:
  - "1921438720"
categories:
  - C or C++
---
#### Hello, Guys let&#8217;s have a fun, i am giving  you a code just tell me what will be the output of this code if you enter there parameters.

<pre>For Test case 1 --&gt;Q
For Test case 2 --&gt;QQ</pre>

#### Please tell why putchar() function is not working and if it is working why it is not taking any Char input?

`<br />
#include <stdio.h><br />
main()<br />
{<br />
putc(getc(stdin),stdout);<br />
putchar(getchar( ));<br />
return 0;<br />
}<br />
` 

#### Explain the output for these test cases.