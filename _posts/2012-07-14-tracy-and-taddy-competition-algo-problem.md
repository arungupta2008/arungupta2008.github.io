---
id: 32
title: Tracy and Taddy Competition (Algo Problem)
date: 2012-07-14T19:04:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=32
permalink: /?p=32
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/07/tracy-and-taddy-competition-algo.html
dsq_thread_id:
  - "1994404713"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  </p> 
  
  <div style="color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    Teddy and Tracy like to play a game based on strings. The game is as follows. Initially, Tracy writes a long random string on a whiteboard. Then, each player starting with Teddy makes turn alternately. Each turn, the player must erase a contiguous substring that exists in the dictionary. The dictionary consists of <i>N</i> words.
  </div>
  
  <div style="color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    Of course, the player that can&#8217;t erase any substring in his turn loses the game, and the other player is declared the winner.
  </div>
  
  <div style="color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    Note that after a substring R is erased, the remaining substring becomes separated, i.e. they cannot erase a word that occurs partially to the left of R and partially to the right of R.
  </div>
  
  <div style="color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    Determine the winner of the game, assuming that both players play optimally.
  </div>
  
  <h3 style="color: #656565; font-family: Arial, Helvetica, sans-serif; font-size: 15px; margin: 8px 0px 12px; padding: 0px; text-align: justify;">
    Input
  </h3>
  
  <div style="color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    The first line contains a single integer <i>T</i>, the number of test cases. <i>T</i> test cases follow. The first line of each testcase contains a string <i>S</i>, the string Tracy writes on the whiteboard. The next line contains a single integer <i>N</i>. <i>N</i> lines follow. The <i>i</i>-th line contains a single string <i>w<sub>i</sub></i>, the <i>i</i>-th word in the dictionary.
  </div>
  
  <h3 style="color: #656565; font-family: Arial, Helvetica, sans-serif; font-size: 15px; margin: 8px 0px 12px; padding: 0px; text-align: justify;">
    Output
  </h3>
  
  <div style="color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    For each test case, output a single line containing the name of the winner of the game.
  </div>
  
  <h3 style="color: #656565; font-family: Arial, Helvetica, sans-serif; font-size: 15px; margin: 8px 0px 12px; padding: 0px; text-align: justify;">
    Example
  </h3>
  
  <pre style="color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; padding: 0px; text-align: justify;"><b>Input:</b><br />3<br />codechef<br />2<br />code<br />chef<br />foo<br />1<br />bar<br />mississippi<br />4<br />ssissi<br />mippi<br />mi<br />ppi<br /><br /><b>Output:</b><br />Tracy<br />Tracy<br />Teddy<br /></pre>
  
  <h3 style="color: #656565; font-family: Arial, Helvetica, sans-serif; font-size: 15px; margin: 8px 0px 12px; padding: 0px; text-align: justify;">
    Constraints
  </h3>
  
  <ul style="color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; list-style-position: inside; margin: 0px; padding: 0px 0px 0px 10px; text-align: justify;">
    <li style="list-style-position: inside; margin: 0px; padding: 0px 0px 0px 10px;">
      1 <= <i>T</i> <= 5
    </li>
    <li style="list-style-position: inside; margin: 0px; padding: 0px 0px 0px 10px;">
      1 <= <i>N</i> <= 30
    </li>
    <li style="list-style-position: inside; margin: 0px; padding: 0px 0px 0px 10px;">
      1 <= |<i>S</i>| <= 30
    </li>
    <li style="list-style-position: inside; margin: 0px; padding: 0px 0px 0px 10px;">
      1 <= |<i>w<sub>i</sub></i>| <= 30
    </li>
    <li style="list-style-position: inside; margin: 0px; padding: 0px 0px 0px 10px;">
      <i>S</i> and <i>w<sub>i</sub></i> contain only characters &#8216;a&#8217;-&#8216;z&#8217;
    </li>
  </ul>
</div>