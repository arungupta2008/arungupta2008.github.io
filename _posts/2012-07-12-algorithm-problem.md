---
id: 33
title: Algorithm Problem
date: 2012-07-12T09:49:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=33
permalink: /?p=33
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/07/algorithm-problem.html
dsq_thread_id:
  - "1768378555"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  <span style="font-size: x-large;">Gift to his Child understand the code if you guys have any problem please let me know .</span> </p> 
  
  <p>
    Our Chef is very happy that his son was selected for training in one of the finest culinary schools of the world. So he and his wife decide to buy a gift for the kid as a token of appreciation. Unfortunately, the Chef hasn&#8217;t been doing good business lately, and is in no mood on splurging money. On the other hand, the boy&#8217;s mother wants to buy something big and expensive. To settle the matter like reasonable parents, they play a game. <br /> They spend the whole day thinking of various gifts and write them down in a huge matrix. Each cell of the matrix contains the gift&#8217;s cost. Then they decide that the mother will choose a row number <b>r</b> while the father will choose a column number <b>c</b>, the item from the corresponding cell will be gifted to the kid in a couple of days. <br /> The boy observes all of this secretly. He is smart enough to understand that his parents will ultimately choose a gift whose cost is <b>smallest</b> in its <b>row</b>, but <b>largest</b> in its <b>column</b>. If no such gift exists, then our little chef has no option but to keep guessing. As the matrix is huge, he turns to you for help. <br /> He knows that sometimes the gift is not determined uniquely even if a gift exists whose cost is smallest in its row, but largest in its column. However, since the boy is so smart, he realizes that the gift&#8217;s <b>cost</b> is determined <b>uniquely</b>. Your task is to tell him the gift&#8217;s <b>cost</b> which is smallest in its row, but largest in its column, or to tell him no such gift exists.
  </p>
  
  <h3>
    Input
  </h3>
  
  <p>
    First line contains two integers <b>R</b> and <b>C</b>, the number of rows and columns in the matrix respectively. Then follow <b>R</b> lines, each containing <b>C</b> space separated integers &#8211; the costs of different gifts.
  </p>
  
  <h3>
    Output
  </h3>
  
  <p>
    Print a single integer &#8211; a value in the matrix that is smallest in its row but highest in its column. If no such value exists, then print &#8220;GUESS&#8221; (without quotes of course)
  </p>
  
  <h3>
    Constraints
  </h3>
  
  <p>
    1 <= <b>R</b>, <b>C</b> <= 100 <br /> All gift costs are positive and less than 100000000 (10^8)
  </p>
  
  <h3>
    Example 1
  </h3>
  
  <pre><b>Input:</b><br />2 3<br />9 8 8<br />2 6 11<br /><br /><b>Output:</b><br />8<br /></pre>
  
  <h3>
    Example 2
  </h3>
  
  <pre><b>Input:</b><br />3 3<br />9 8 11<br />2 6 34<br />5 9 11<br /><br /><b>Output:</b><br />GUESS<br /></pre>
  
  <h3>
    Example 3
  </h3>
  
  <pre><b>Input:</b><br />2 2<br />10 10<br />10 10<br /><br /><b>Output:</b><br />10<br /></pre>
</div>