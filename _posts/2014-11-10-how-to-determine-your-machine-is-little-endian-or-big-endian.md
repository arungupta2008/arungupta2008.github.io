---
id: 495
title: 'How to determine your machine is &#8220;Little Endian&#8221; or &#8220;Big Endian&#8221;.'
date: 2014-11-10T18:15:44+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=495
permalink: /?p=495
dsq_thread_id:
  - "4753649412"
categories:
  - "Geek's Stuffs"
tags:
  - Algorithm
  - C
  - Interesting
  - Linux
  - Technical
---
##### What is big and Little Endian ?

Little and big endian are two ways of storing multibyte data-types ( int, float, etc). In little endian machines, last byte of binary representation of the multibyte data-type is stored first. On the other hand, in big endian machines, first byte of binary representation of the multibyte data-type is stored first.

[Big Endian(Wikipedia)](http://en.wikipedia.org/wiki/File:Big-Endian.svg)

[Little Endian(Wikipedia)](http://en.wikipedia.org/wiki/File:Little-Endian.svg)

**Is there a quick way to determine endianness of your machine?**
  
There are n no. of ways for determining endianness of your machine. Here is one quick way of doing the same.

<div class="line number1 index0 alt2">
  <span style="color: #ff0000;"><code class="cpp preprocessor">#include &lt;stdio.h&gt;</code></span>
</div>

<div class="line number2 index1 alt1">
  <span style="color: #ff0000;"><code class="cpp color1 bold">int</code> <code class="cpp plain">main() </code></span>
</div>

<div class="line number3 index2 alt2">
  <span style="color: #ff0000;"><code class="cpp plain">{</code></span>
</div>

<div class="line number4 index3 alt1">
  <span style="color: #ff0000;"><code class="cpp spaces">   </code><code class="cpp plain">unsigned </code><code class="cpp color1 bold">int</code> <code class="cpp plain">i = 1;</code></span>
</div>

<div class="line number5 index4 alt2">
  <span style="color: #ff0000;"><code class="cpp spaces">   </code><code class="cpp color1 bold">char</code> <code class="cpp plain">*c = (</code><code class="cpp color1 bold">char</code><code class="cpp plain">*)&i;</code></span>
</div>

<div class="line number6 index5 alt1">
  <span style="color: #ff0000;"><code class="cpp spaces">   </code><code class="cpp keyword bold">if</code> <code class="cpp plain">(*c)    </code></span>
</div>

<div class="line number7 index6 alt2">
  <span style="color: #ff0000;"><code class="cpp spaces">       </code><code class="cpp functions bold">printf</code><code class="cpp plain">(</code><code class="cpp string">"Little endian"</code><code class="cpp plain">);</code></span>
</div>

<div class="line number8 index7 alt1">
  <span style="color: #ff0000;"><code class="cpp spaces">   </code><code class="cpp keyword bold">else</code></span>
</div>

<div class="line number9 index8 alt2">
  <span style="color: #ff0000;"><code class="cpp spaces">       </code><code class="cpp functions bold">printf</code><code class="cpp plain">(</code><code class="cpp string">"Big endian"</code><code class="cpp plain">);</code></span>
</div>

<div class="line number10 index9 alt1">
  <span style="color: #ff0000;"><code class="cpp spaces">   </code><code class="cpp functions bold">getchar</code><code class="cpp plain">();</code></span>
</div>

<div class="line number11 index10 alt2">
  <span style="color: #ff0000;"><code class="cpp spaces">   </code><code class="cpp keyword bold">return</code> <code class="cpp plain">0;</code></span>
</div>

<div class="line number12 index11 alt1">
  <span style="color: #ff0000;"><code class="cpp plain">}</code></span>
</div>

<div class="line number12 index11 alt1">
</div>

In the above program, a character pointer c is pointing to an integer i. Since size of character is 1 byte when the character pointer is de-referenced it will contain only first byte of integer. If machine is little endian then \*c will be 1 (because last byte is stored first) and if machine is big endian then \*c will be 0.