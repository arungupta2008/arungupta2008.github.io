---
id: 24
title: Write a program to find if a tree is symmetric.
date: 2012-09-09T18:55:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=24
permalink: /?p=24
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/09/write-program-to-find-if-tree-is.html
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  Solution #1: A symmetric binary tree is one where if you draw a vertical line passing through the root node then the left half should be the mirror image of the right half. Here is the recursive code,</p> 
  
  <p>
  </p>
  
  <pre><span>int</span><span> isSymmetric</span><span>(</span><span>struct</span><span> node</span><span>*</span><span> l</span><span>,</span><span> </span><span>struct</span><span> node</span><span>*</span><span> r</span><span>)</span><span><br /></span><span>{</span><span><br />    </span><span>if</span><span>((</span><span>l </span><span>==</span><span> NULL</span><span>)</span><span> </span><span>&&</span><span> </span><span>(</span><span>r </span><span>==</span><span> NULL</span><span>))</span><span><br />        </span><span>return</span><span> </span><span>1</span><span>;</span><span><br /><br />    </span><span>if</span><span>(((</span><span>l </span><span>==</span><span> NULL</span><span>)</span><span> </span><span>&&</span><span> </span><span>(</span><span>r </span><span>!=</span><span> NULL</span><span>))</span><span> </span><span>||</span><span> <br />            </span><span>((</span><span>l </span><span>!=</span><span> NULL</span><span>)</span><span> </span><span>&&</span><span> </span><span>(</span><span>r </span><span>==</span><span> NULL</span><span>)))</span><span><br />        </span><span>return</span><span> </span><span></span><span>;</span><span><br /><br />    </span><span>return</span><span> isSymmetric</span><span>(</span><span>l</span><span>-></span><span>left</span><span>,</span><span> r</span><span>-></span><span>right</span><span>)</span><span> </span><span>&&</span><span> isSymmetric</span><span>(</span><span>l</span><span>-></span><span>right</span><span>,</span><span> r</span><span>-></span><span>left</span><span>);</span><span><br /></span><span>}</span></pre>
</div>