---
id: 28
title: Chefs new Pet
date: 2012-08-04T14:29:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=28
permalink: /?p=28
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/08/chefs-new-pet.html
dsq_thread_id:
  - "5398726446"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  One More Logical Question :</p> 
  
  <p>
  </p>
  
  <div style="background-color: white; color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    The chef got a new rabbit and he is going to train him so that he can perform for him whenever he needs entertainment. The chef teaches k types of jumps to the rabbit. Each jump has definite length L units. The rabbit does not have any brains he will use any type of jump he feels like at any point of time. He is placed on a very long mat and starts at 0 unit. The chef wants to know in how many ways he can perform his jumps and cover exactly N units of distance.
  </div>
  
  <h3 style="background-color: white; color: #656565; font-family: Arial, Helvetica, sans-serif; font-size: 15px; margin: 8px 0px 12px; padding: 0px; text-align: justify;">
    Input
  </h3>
  
  <div style="background-color: white; color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    The first line contains the number of the test cases T(<=100). Each test case consists of 2 lines. The first line defines the distance N (1<=N<=10^18) which tells us the number of units the chef wants the rabbit to cover. The next line contains k the number of jumps which are taught to the rabbit, k (k<=15) integers follow in the same line each denoting distinct distance L (L<=15) units which can be jumped by the rabbit.
  </div>
  
  <h3 style="background-color: white; color: #656565; font-family: Arial, Helvetica, sans-serif; font-size: 15px; margin: 8px 0px 12px; padding: 0px; text-align: justify;">
    Output
  </h3>
  
  <div style="background-color: white; color: #444444; font-family: Arial, sans-serif; font-size: 12px; line-height: 1.5em; padding: 2px 4px; text-align: justify;">
    Print T integers each denoting the number of ways the rabbit can perform jumps of N units of distance. Print the remainder obtained on dividing the answer by 1000000007 if the answer is greater than or equal to 1000000007.
  </div>
  
  <h3 style="background-color: white; color: #656565; font-family: Arial, Helvetica, sans-serif; font-size: 15px; margin: 8px 0px 12px; padding: 0px; text-align: justify;">
    Example
  </h3>
  
  <pre style="background-color: white; color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; padding: 0px; text-align: justify;"><b>Input:</b><br />3<br />10<br />1 1<br />13<br />3 1 2 8<br />15<br />5 1 2 3 4 5<br /><br /><br /><br /><b>Output:</b><br />1<br />415<br />13624</pre>
  
  <pre style="background-color: white; color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; padding: 0px; text-align: justify;"><br /></pre>
  
  <pre style="background-color: white; color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; padding: 0px; text-align: justify;"><br /></pre>
  
  <pre style="background-color: white; color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; padding: 0px; text-align: justify;">i have coded That My self</pre>
  
  <pre style="background-color: white; color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; padding: 0px; text-align: justify;"><br /></pre>
  
  <pre style="background-color: white; padding: 0px; text-align: justify;"><span style="color: #444444; font-family: Courier New, Courier, monospace;"><span style="font-size: 12px;">import java.util.*;<br />public class RabbitJumpMine<br />{<br /> static int count = 0;<br /> public static void main (String [] args)<br /> {<br />  Scanner sc = new Scanner(System.in);<br />  int test = sc.nextInt();<br />  int temp = 0;<br />  while(test != 0)<br />  {       <br />   int Counts = 0;<br />   int n = sc.nextInt();<br />   int k = sc.nextInt();<br />   int [] arr = new int[k]; <br />   /*System.out.println("**********");<br />   for(int i= 0 ; i&lt;k ;++i)<br />   {<br />    System.out.println(arr[i]);<br />   }<br />   System.out.println("**********");*/<br />   for(int i =0 ; i&lt;k ; i++)<br />   {<br />    temp = sc.nextInt(); <br />    if(temp > n)<br />    {<br />    --i;<br />    --k;<br />    continue;<br />    }<br />    else<br />    arr[i] = temp; <br />   }<br />   /*System.out.println("**"+k);<br />   System.out.println("**********");<br />   for(int i= 0 ; i&lt;k ;++i)<br />   {<br />    System.out.println(arr[i]);<br />   }<br />   System.out.println("**********");<br />   */<br />   //Finding Counts<br />   for(int i= 0 ; i&lt;k ;++i)<br />   {<br />   Counts = Counts + Countss(arr[i],n,arr,k, n);<br />   count = 0 ;<br />   }<br />   System.out.println(Counts);<br />  --test;  <br />  }<br />  <br />  <br /> }<br /><br />   static int Countss(int a , int b , int cArray[] ,int k ,int n )<br />   {<br />    int temp = 0;<br />     <br />    if(a==b)<br />    {<br />     ++count;<br />     return count;<br />    }<br />    else<br />    {<br />     b = b-a;<br />     for(int i = 0 ; i &lt; k ;++i)<br />     {<br />      if(cArray[i] &lt;= b){<br />      temp =  Countss(cArray[i] , b ,cArray, k , n);<br />       }<br />     }    <br />    }<br />   return count;<br />   } <br />}</span></span></pre>
  
  <pre style="background-color: white; color: #444444; font-family: Arial, Helvetica, sans-serif; font-size: 12px; padding: 0px; text-align: justify;"> </pre>
</div>