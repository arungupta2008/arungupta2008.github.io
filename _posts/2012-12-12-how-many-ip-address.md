---
id: 8
title: How Many Ip Address !!!
date: 2012-12-12T06:28:29+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=8
permalink: /?p=8
dsq_thread_id:
  - "1768378398"
categories:
  - Algorithm
  - C or C++
  - Uncategorized
tags:
  - Algorithm
  - Coding
---
Given a string containing only digits, restore it by returning all possible valid IP address combinations.
  
For example:
  
Given &#8220;25525511135&#8221;,
  
return [&#8220;255.255.11.135&#8221;, &#8220;255.255.111.35&#8221;]{hint:recursion,backtrack}

Here is the Solution &#8230;&#8230;
  
it was taken me about 5 hours to solve see !!!

//cc Arun Kumar Gupta

import java.util.*;
  
public class AllIpAddress
  
{
  
public static void main (String [] args)
  
{
  
Scanner sc = new Scanner(System.in);
  
String input = sc.next();
  
int[] intArray = new int[input.length()];
  
int length = input.length();

for (int i = 0; i < input.length(); i++) {
  
intArray[i] = Character.digit(input.charAt(i), 10);
  
//System.out.println(intArray[i]);
  
}
  
int i = 0 , j = 1 , k = 2;
  
AllIpAddress ip = new AllIpAddress();
  
ip.Ipaddress(intArray , i , j , k , length-1);

}
  
void Ipaddress(int [] intArray , int i , int j , int k , int length)
  
{
  
try{
  
int where = 0 ,change = 0;
  
int p1 =createIP( intArray , -1 , i);
  
int p2 =createIP( intArray , i ,  j );
  
int p3 =createIP( intArray ,  j , k );
  
int p4 =createIP( intArray ,  k ,  length );
  
//System.out.println(&#8220;\***\***\****Garbage&#8221;+p1+&#8221;.&#8221;+p2+&#8221;.&#8221;+p3+&#8221;.&#8221;+p4);
  
//System.out.println(&#8220;i = &#8220;+i+&#8221;j = &#8220;+j+&#8221;k = &#8220;+k);
  
if((p1<=255)&&(p2<=255)&&(p3<=255)&&(p4<=255)&&(p4>0))
  
{
  
System.out.println(p1+&#8221;.&#8221;+p2+&#8221;.&#8221;+p3+&#8221;.&#8221;+p4);
  
}
  
if(p4 >255)
  
{
  
//if(k != j)
  
//++k;
  
where =4;
  
//System.out.println(&#8220;Problem at P4&#8221;);
  
}
  
else if(p3>255)
  
{
  
//if(j != i)
  
//++j;
  
//&#8211;k;
  
where = 3;
  
//System.out.println(&#8220;Problem at P3&#8221;);
  
}
  
else if(p2>255)
  
{
  
//++i;
  
where = 2;
  
//System.out.println(&#8220;Problem at P2&#8221;);
  
}
  
else if(p1>255)
  
{

//System.out.println(&#8220;Problem at P1&#8221;);
  
System.exit(0);
  
}

if((k == length) && (j+1 == k))
  
{
  
//System.out.println(&#8220;if((k == length) && (j+1 == k))&#8221;);
  
//System.out.println(i+&#8221;\_&#8221;+j+&#8221;\_&#8221;+k);
  
++i;
  
j = i+1;
  
k = j+1;
  
change = 1;
  
//System.out.println(i+&#8221;\_&#8221;+j+&#8221;\_&#8221;+k);

}
  
if((k == length) &&(change == 0) )
  
{
  
//System.out.println(&#8220;if((k == length) &&(change == 0) )&#8221;);
  
++j;
  
k = j+1;
  
change = 0;
  
}
  
else if(change == 0)
  
{
  
if( (k) < length )
  
++k;
  
}
  
/*if(where ==4)
  
{
  
++k;
  
}
  
if(where ==3)
  
{
  
++j;
  
&#8211;k;
  
}
  
if(where ==2)
  
{
  
++i;
  
&#8211;j;
  
}
  
/*if(k==length)
  
{
  
&#8211;k;
  
&#8211;j;
  
}*/
  
Ipaddress(intArray , i , j , k , length);
  
}
  
catch(ArrayIndexOutOfBoundsException e){
  
//System.out.println(&#8220;Exception thrown  :&#8221; + e);
  
}
  
}
  
static int createIP(int [] intArray , int start , int end)
  
{
  
//System.out.println(&#8220;I am at createIP()start = &#8220;+start+&#8221;\tend = &#8220;+end);
  
int val = 1 , fina = 0;
  
for(int e =end ; e>start ; &#8211;e)
  
{
  
fina = intArray[e]*val + fina;
  
val = val*10;
  
}
  
return fina;
  
}
  
}