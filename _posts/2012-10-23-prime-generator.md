---
id: 18
title: Prime Generator
date: 2012-10-23T08:57:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=18
permalink: /?p=18
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/10/prime-generator.html
dsq_thread_id:
  - "1768378406"
categories:
  - Algorithm
  - C or C++
  - "Geek's Stuffs"
  - Uncategorized
tags:
  - Algorithm
  - Coding
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  </p> 
  
  <div style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 13px; text-align: justify;">
    Sorry for late post i was too busy &#8230;.
  </div>
  
  <div style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 13px; text-align: justify;">
    this is a new problem 
  </div>
  
  <div style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 13px; text-align: justify;">
  </div>
  
  <div style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 13px; text-align: justify;">
    Peter wants to generate some prime numbers for his cryptosystem. Help him! Your task is to generate all prime numbers between two given numbers!
  </div>
  
  <h3 style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 15px; text-align: center;">
    Input
  </h3>
  
  <div style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 13px; text-align: justify;">
    The input begins with the number t of test cases in a single line (t<=10). In each of the next t lines there are two numbers m and n (1 <= m <= n <= 1000000000, n-m<=100000) separated by a space.
  </div>
  
  <h3 style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 15px; text-align: center;">
    Output
  </h3>
  
  <div style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 13px; text-align: justify;">
    For every test case print all prime numbers p such that m <= p <= n, one number per line, test cases separated by an empty line.
  </div>
  
  <h3 style="background-color: #f6f9e0; color: #000020; font-family: Verdana, Arial, Helvetica, sans-serif; font-size: 15px; text-align: center;">
    Example
  </h3>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"><b>Input:</b><br />2<br />1 10<br />3 5<br /><br /><b>Output:</b><br />2<br />3<br />5<br />7<br /><br />3<br />5</pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;">Solution :</pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;">CC Arun Kumar Gupta</pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0;"><span style="color: #000020;">import java.util.*;<br />public class FastestPrime<br />{<br /> public static void main (String [] args)<br /> {<br />  Scanner sc = new Scanner(System.in);<br />  int test_cases = sc.nextInt();<br />  if((test_cases &lt;=10) &#038;&#038; (test_cases > 0))<br />  {<br />  for(int i = 0 ; i&lt;test_cases ; ++i)<br />   {<br />    int m = sc.nextInt();<br />    int n = sc.nextInt();<br />    if((m&lt;= 1000000000) &#038;&#038;(n&lt;=1000000000)&#038;&#038;(n>0)&&(m>0))<br />    {<br />    if((n-m) &lt;= 100000)<br />    {<br />     if((m % 2) == 0)<br />     ++m;<br />     for(int j = m ; j&lt;= n ; ++j)<br />     {<br />      NextNum(j);<br />      j = j+ 1;<br />      <br />     }     <br />    }<br />    }<br />  System.out.println(); <br />   }<br />  }<br />  <br /><br /> }<br /> static void  NextNum(int m)<br /> {<br />  int div = 3;<br />  int array [] = new int[1000];<br />  int rem  = 1 ;<br />  while((rem != 0) && (div &lt;= (m/2)))<br />   {<br />    rem = m%div;<br />    div = div+2;<br />   }<br />  if(rem != 0)<br />  {<br />  System.out.println(m);<br />   }<br />  <br /> }<br />}</span></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
  
  <pre style="background-color: #f6f9e0; color: #000020; font-size: 13px;"></pre>
</div>