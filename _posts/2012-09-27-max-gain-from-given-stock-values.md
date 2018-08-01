---
id: 21
title: Max gain from given stock values
date: 2012-09-27T07:53:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=21
permalink: /?p=21
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/09/max-gain-from-given-stock-values.html
dsq_thread_id:
  - "1795627209"
categories:
  - Uncategorized
tags:
  - Algorithm
  - Coding
---
<div dir="ltr" style="text-align: left;">
  <span style="font-family: Arial, Helvetica, sans-serif;"><br /> </span><span style="font-family: Arial, Helvetica, sans-serif;"><br /> </span><span style="font-family: Arial, Helvetica, sans-serif;">Given ticker value for a stock, for next n days, given what is the max profit that you can make ?</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">Eg &#8211; the max profit you can make is buy at time t1 @ 5 and sell @ t2 when stock was 12, to get max Profit of 7 dollars.</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;"><br /> time &#8211; Stock Price</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">t0 &#8211; 10</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">t1 &#8211; 5</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">t2 &#8211; 12</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">t3 &#8211; 7</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">t4 &#8211; 12</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;"><br /> Also &#8211; you can only trade once i.e you can buy and sell only 1 time.</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">so here is the solution of that problem .that problem is nothing just think like that if we have only one day stock values so we can buy or sell on that day only , so for general we can find the for up to kth day and we can find out for the k+1&#8217;th day ..</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;"><br /> so algo is that maintain the 3 things first two pointer of buy and sell and one pointer of minimum values .we can make it in O(n) only</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;"><br /> </span><span style="font-family: Arial, Helvetica, sans-serif;"><br /> Just make a new array which contains the &#8220;lookahead&#8221; view, where we can see, which potential highest value we can gaini in future.</span><br /> <span style="font-family: Arial, Helvetica, sans-serif;">Another array just contains the lowest value so far. When the difference between the two arrays is max, there is the buying point. Selling point is, when the falling edge of the max array is reached.</span><br /> <code>&lt;br />
&lt;span style="font-family: Arial, Helvetica, sans-serif;">&lt;br />
&lt;/span>&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b> public void highestGain(int[] prices) {&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        int[] maxPrices = new int[prices.length];&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        int[] minPrices = new int[prices.length];&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        maxPrices[maxPrices.length-1] = prices[prices.length-1];&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        minPrices[0] = prices[0];&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        for(int i = 1; i &lt;prices.length; i++) {&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            int right = prices.length-i-1;&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            minPrices[i] = Math.min(minPrices[i-1], prices[i]);&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            maxPrices[right] = Math.max(maxPrices[right+1], prices[right]);&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        }&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        System.out.println("MaxPrices: " + Arrays.toString(maxPrices));&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        System.out.println("MinPrices: " + Arrays.toString(minPrices));&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>&lt;br />
// find when to buy (when the difference of min/max is highest)&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        int maxDifference = maxPrices[0] - minPrices[0];&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        int maxDifferencePos = 0;&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        for(int i=0; i&lt;minPrices.length; i++) {&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            int difference = maxPrices[i] - minPrices[i];&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            if(maxDifference &lt; difference) {&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>                maxDifference = difference;&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>                maxDifferencePos = i;&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            }&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        }&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        // Now find the falling edge of max prices - there was the last peak&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        int sellPos = maxDifferencePos+1;&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        int lastPrice = maxPrices[maxDifferencePos];&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        for(; sellPos &lt; maxPrices.length; sellPos++) {&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            if(lastPrice &gt; maxPrices[sellPos]) {&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>                sellPos --;&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>                break;&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>            }&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>        }&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>&lt;br />
System.out.println("Ideal to buy/sell: " + maxDifferencePos + ":" + sellPos);&lt;/b>&lt;/span>&lt;br />
&lt;span style="font-family: Courier New, Courier, monospace;">&lt;b>    }&lt;/b>&lt;/span>&lt;/p>
&lt;p>&lt;span style="font-family: Arial, Helvetica, sans-serif;">&lt;br />
&lt;/span>&lt;span style="font-family: Courier New, Courier, monospace;">&lt;br />
&lt;/span>&lt;/div>
&lt;p></code></p>