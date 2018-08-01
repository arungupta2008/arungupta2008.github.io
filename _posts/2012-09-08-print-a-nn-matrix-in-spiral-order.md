---
id: 25
title: 'Print a n*n matrix in spiral order'
date: 2012-09-08T12:11:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=25
permalink: /?p=25
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/09/print-nn-matrix-in-spiral-order.html
dsq_thread_id:
  - "1768378497"
categories:
  - Uncategorized
---
<div dir="ltr" style="text-align: left;" trbidi="on">
  <span style="font-family: inherit;">Print a n*n matrix in spiral order and what will be the consequences(if u use recursion) in case of larger matrices like 10000*10000</span></p> 
  
  <p>
    <span style="font-family: inherit;">we can not use the recursion b&#8217;coz stack overflow may occur.</span><br /><span style="font-family: inherit;">so we can not use the recursion !!!</span><br /><span style="font-family: "Courier New", Courier, monospace;"><span style="font-family: inherit;">cc to Arun Kumar Gupta !!</span>
  </p>
  
  <p>
    import java.util.*;<br />import java.lang.*;<br />public class MatrixWithRotation_In_Java<br />{<br />    public static void main (String [] args)<br />    {<br />        Scanner sc = new Scanner(System.in);<br />        int n = sc.nextInt();<br />        System.out.println(n+&#8221;\n&#8221;);<br />        <br />        int [][] a = new int[n][n];<br />        String stat = &#8220;RR&#8221;;<br />        int i=0 , j = 0 , el = 0 , c= 0 ,eu = 1 , cb = n-1 , rb = n-1 , change = 1 ;<br />        System.out.println(&#8220;cb :&#8221;+cb+&#8221;\n&#8221;);<br />        System.out.println(&#8220;rb :&#8221;+rb+&#8221;\n&#8221;);<br />        for(int k = 0 ; k<(n*n + 20) ; ++k)<br />        //while(a[i][j] == 0)<br />        {<br />            if(change == 1)<br />            {<br />            System.out.println(i+&#8221;\t&#8221; + j +&#8221;\n&#8221;);<br />            ++c;<br />            a[i][j] = c;<br />            }<br />            <br />            <br />            if(stat.equals(&#8220;RR&#8221;))    <br />            {<br />                System.out.println(&#8220;RR\n&#8221;);<br />                if(j+1<=cb)<br />                {<br />                change = 1;<br />                ++j;}    <br />                <br />                else<br />                {<br />                    stat = &#8220;CD&#8221;;<br />                    &#8211;cb;    <br />                    change = 0;        <br />                }<br />            }<br />            <br />            if(stat.equals(&#8220;CD&#8221;))    <br />            {<br />                System.out.println(&#8220;CD\n&#8221;);<br />                if(i+1<=rb)<br />                {<br />                ++i;<br />                change = 1;<br />                }    <br />                else<br />                {<br />                    stat = &#8220;RL&#8221;;<br />                    &#8211;rb;    <br />                    change = 0;        <br />                }<br />            }<br />            if(stat.equals(&#8220;RL&#8221;))    <br />            {<br />                System.out.println(&#8220;RL\n&#8221;);<br />                if(j-1>=el)<br />                {<br />                &#8211;j;<br />                change = 1;<br />                }    <br />                else<br />                {<br />                    stat = &#8220;CU&#8221;;<br />                    change = 0;    <br />                    ++el;        <br />                }<br />            }<br />            if(stat.equals(&#8220;CU&#8221;))    <br />            {<br />                System.out.println(&#8220;CU\n&#8221;);<br />                if((i-1>=eu) )<br />                {<br />                &#8211;i;<br />                change = 1;<br />                }    <br />                else<br />                {<br />                    stat = &#8220;RR&#8221;;<br />                    ++eu;    <br />                    change = 0;    <br />                }<br />            }<br />            <br />        }<br />        for(int k = 0 ; k<n ; ++k)<br />        {<br />            for(int l = 0 ; l<n ; ++l)<br />            {<br />                System.out.print(a[k][l]+&#8221;\t&#8221;);<br />            }<br />            System.out.print(&#8220;\n&#8221;);<br />        }<br />            <br />    <br />    }<br />}</span></div>