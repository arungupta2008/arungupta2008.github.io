---
id: 23
title: How Many Ip Address !!!
date: 2012-09-15T12:40:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=23
permalink: /?p=23
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/09/how-many-ip-address.html
dsq_thread_id:
  - "1768378438"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;">
  Hi Friends new problem<span style="color: #e06666;"><span style="font-size: large;">Given a string containing only digits, restore it by returning all possible valid IP address combinations.</span></span><br /> <span style="color: #e06666;"><span style="font-size: large;">For example:<br /> Given &#8220;25525511135&#8221;,</span></span><br /> <span style="color: #e06666;"><span style="font-size: large;">return [&#8220;255.255.11.135&#8221;, &#8220;255.255.111.35&#8221;]{hint:recursion,backtrack}</span></span><br /> <span style="color: #e06666;"><br /> </span><span style="color: #e06666;"><br /> </span><span style="color: #e06666;"><span style="color: black;">Here is the Solution &#8230;&#8230; </span></span><br /> <span style="color: #e06666;"><span style="color: black;">it was taken me about 5 hours to solve see !!!</span></span><br /> <code>&lt;br />
&lt;span style="color: #e06666;">&lt;span style="color: black;">&lt;span>//cc Arun Kumar Gupta&lt;/span>&lt;/span>&lt;/span>&lt;/p>
&lt;p>import java.util.*;&lt;br />
public class AllIpAddress&lt;br />
{&lt;br />
public static void main (String [] args)&lt;br />
{&lt;br />
Scanner sc = new Scanner(System.in);&lt;br />
String input = sc.next();&lt;br />
int[] intArray = new int[input.length()];&lt;br />
int length = input.length();&lt;/p>
&lt;p>for (int i = 0; i &lt; input.length(); i++) {&lt;br />
intArray[i] = Character.digit(input.charAt(i), 10);&lt;br />
//System.out.println(intArray[i]);&lt;br />
}&lt;br />
int i = 0 , j = 1 , k = 2;&lt;br />
AllIpAddress ip = new AllIpAddress();&lt;br />
ip.Ipaddress(intArray , i , j , k , length-1);&lt;/p>
&lt;p>}&lt;br />
void Ipaddress(int [] intArray , int i , int j , int k , int length)&lt;br />
{&lt;br />
try{&lt;br />
int where = 0 ,change = 0;&lt;br />
int p1 =createIP( intArray , -1 , i);&lt;br />
int p2 =createIP( intArray , i ,  j );&lt;br />
int p3 =createIP( intArray ,  j , k );&lt;br />
int p4 =createIP( intArray ,  k ,  length );&lt;br />
//System.out.println("**********Garbage"+p1+"."+p2+"."+p3+"."+p4);&lt;br />
//System.out.println("i = "+i+"j = "+j+"k = "+k);&lt;br />
if((p1&lt;=255)&&(p2&lt;=255)&&(p3&lt;=255)&&(p4&lt;=255)&&(p4&gt;0))&lt;br />
{&lt;br />
System.out.println(p1+"."+p2+"."+p3+"."+p4);&lt;br />
}&lt;br />
if(p4 &gt;255)&lt;br />
{&lt;br />
//if(k != j)&lt;br />
//++k;&lt;br />
where =4;&lt;br />
//System.out.println("Problem at P4");&lt;br />
}&lt;br />
else if(p3&gt;255)&lt;br />
{&lt;br />
//if(j != i)&lt;br />
//++j;&lt;br />
//--k;&lt;br />
where = 3;&lt;br />
//System.out.println("Problem at P3");&lt;br />
}&lt;br />
else if(p2&gt;255)&lt;br />
{&lt;br />
//++i;&lt;br />
where = 2;&lt;br />
//System.out.println("Problem at P2");&lt;br />
}&lt;br />
else if(p1&gt;255)&lt;br />
{&lt;/p>
&lt;p>//System.out.println("Problem at P1");&lt;br />
System.exit(0);&lt;br />
}&lt;/p>
&lt;p>if((k == length) && (j+1 == k))&lt;br />
{&lt;br />
//System.out.println("if((k == length) && (j+1 == k))");&lt;br />
//System.out.println(i+"_"+j+"_"+k);&lt;br />
++i;&lt;br />
j = i+1;&lt;br />
k = j+1;&lt;br />
change = 1;&lt;br />
//System.out.println(i+"_"+j+"_"+k);&lt;/p>
&lt;p>}&lt;br />
if((k == length) &&(change == 0) )&lt;br />
{&lt;br />
//System.out.println("if((k == length) &&(change == 0) )");&lt;br />
++j;&lt;br />
k = j+1;&lt;br />
change = 0;&lt;br />
}&lt;br />
else if(change == 0)&lt;br />
{&lt;br />
if( (k) &lt; length )&lt;br />
++k;&lt;br />
}&lt;br />
/*if(where ==4)&lt;br />
{&lt;br />
++k;&lt;br />
}&lt;br />
if(where ==3)&lt;br />
{&lt;br />
++j;&lt;br />
--k;&lt;br />
}&lt;br />
if(where ==2)&lt;br />
{&lt;br />
++i;&lt;br />
--j;&lt;br />
}&lt;br />
/*if(k==length)&lt;br />
{&lt;br />
--k;&lt;br />
--j;&lt;br />
}*/&lt;br />
Ipaddress(intArray , i , j , k , length);&lt;br />
}&lt;br />
catch(ArrayIndexOutOfBoundsException e){&lt;br />
//System.out.println("Exception thrown  :" + e);&lt;br />
}&lt;br />
}&lt;br />
static int createIP(int [] intArray , int start , int end)&lt;br />
{&lt;br />
//System.out.println("I am at createIP()start = "+start+"\tend = "+end);&lt;br />
int val = 1 , fina = 0;&lt;br />
for(int e =end ; e&gt;start ; --e)&lt;br />
{&lt;br />
fina = intArray[e]*val + fina;&lt;br />
val = val*10;&lt;br />
}&lt;br />
return fina;&lt;br />
}&lt;br />
}&lt;br />
&lt;span style="color: #e06666;">&lt;span style="color: black;"> &lt;/span>&lt;/span>&lt;/p>
&lt;/div>
&lt;p></code></p>