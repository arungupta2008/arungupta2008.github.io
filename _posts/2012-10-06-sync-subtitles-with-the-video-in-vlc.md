---
id: 20
title: Sync Subtitles With The Video In VLC
date: 2012-10-06T11:19:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=20
permalink: /?p=20
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/10/sync-subtitles-with-video-in-vlc.html
dsq_thread_id:
  - "1830968614"
categories:
  - Algorithm
  - C or C++
  - "Geek's Stuffs"
  - Uncategorized
tags:
  - Linux
  - Technical
  - VLC
---
<div dir="ltr" style="text-align: left;">
  <div style="background-color: white; color: #333333; font-family: Ubuntu, 'Segoe UI', Helvetica, Georgia, sans-serif; font-size: 13px; line-height: 21px; margin-bottom: 10px; margin-top: 10px; padding: 0px; text-align: justify;">
  </div>
  
  <div style="clear: both; text-align: justify;">
    <a style="margin-left: 1em; margin-right: 1em;" href="http://cdn.pctonic.netdna-cdn.com/media/2010/05/Screenshot125.png"><img alt="" src="http://cdn.pctonic.netdna-cdn.com/media/2010/05/Screenshot125.png" width="400" height="310" border="0" /></a>
  </div>
  
  <div style="background-color: white; color: #333333; font-family: Ubuntu, 'Segoe UI', Helvetica, Georgia, sans-serif; font-size: 13px; line-height: 21px; margin-bottom: 10px; margin-top: 10px; padding: 0px; text-align: justify;">
  </div>
  
  <div style="background-color: white; color: #333333; font-family: Ubuntu, 'Segoe UI', Helvetica, Georgia, sans-serif; font-size: 13px; line-height: 21px; margin-bottom: 10px; margin-top: 10px; padding: 0px; text-align: justify;">
    I can’t stress the usefulness of subtitles enough, especially when you’re watching a movie in a foreign language. I was watching Heavenly Forest, a Japanese romantic drama, a few days back. The movie was wonderful, but I wouldn’t have understood anything had it not been for those English subtitles. I even tend to use English subtitles while watching<em>English</em> movies, because you guys talk so fast (Americans) or so weird (British) that it’s hard for me to grasp!
  </div>
  
  <div style="background-color: white; color: #333333; font-family: Ubuntu, 'Segoe UI', Helvetica, Georgia, sans-serif; font-size: 13px; line-height: 21px; margin-bottom: 10px; margin-top: 10px; padding: 0px; text-align: justify;">
    Handy as they are, subtitles can turn extremely irritating if they’re out of sync with the video. They distract you, and you end up understanding even less than what you’d have without the subs. Thankfully, if you’re using <a style="color: #4488dd; text-decoration: none;" href="http://videolan.org/">VLC player</a> to watch the videos, you can make use of a nifty feature in the program to sync the subtitle with the video! Do note that it’ll only temporarily sync the subtitles with the video, and the sync will be gone the next time you watch the video.
  </div>
  
  <div style="background-color: white; color: #333333; font-family: Ubuntu, 'Segoe UI', Helvetica, Georgia, sans-serif; font-size: 13px; line-height: 21px; margin-bottom: 10px; margin-top: 10px; padding: 0px; text-align: justify;">
    Anyway, lets get started with how to implement it. I’m assuming that you’ve already loaded the video and subtitle files into VLC (you can just drag them both into its interface). Now, carefully take a look at the video and the subs, and see whether the subs are lagging behind or running ahead of the video. If you’re watching a foreign movie, it may seem like a very difficult job, but just try a little hard and you should be able to make this out. For example, if you see a girl screaming and running around wildly, and the subs show “Help me! Help me!” 3 seconds after that scene, this means that the titles are 3 seconds behind the movie.
  </div>
  
  <div style="background-color: white; color: #333333; font-family: Ubuntu, 'Segoe UI', Helvetica, Georgia, sans-serif; font-size: 13px; line-height: 21px; margin-bottom: 10px; margin-top: 10px; padding: 0px; text-align: justify;">
    Once you’ve figured out the lag / lead of the subtitle, it’s time to sync it with the video. In VLC, navigate to <em>Tools > Track Synchronization</em>, where you’ll find the <em>Subtitles/Video</em> section. Now comes the important part – syncing the subtitle. If the subtitle is lagging behind the video, you’ve to provide a negative value to ‘<em>Advance of subtitles over video’</em>. Say the subs display 3 seconds after the video, the value you got to enter is –3.000 s. Note that you can adjust the sync time to upto a thousandth of a second, although adjusting to the tenths does the job in all cases. Similarly if the subtitle is ahead of the video, enter the required positive number of seconds. Hit the Refresh button at the top right corner of the window, and you should see the change immediately.
  </div>
  
  <div style="clear: both; text-align: justify;">
    <a style="margin-left: 1em; margin-right: 1em;" href="http://cdn.pctonic.netdna-cdn.com/media/2010/05/Screenshot126.png"><img alt="" src="http://cdn.pctonic.netdna-cdn.com/media/2010/05/Screenshot126.png" width="400" height="240" border="0" /></a>
  </div>
  
  <div style="clear: both; text-align: justify;">
    <a style="margin-left: 1em; margin-right: 1em;" href="http://cdn.pctonic.netdna-cdn.com/media/2010/05/Screenshot127.png"><img alt="" src="http://cdn.pctonic.netdna-cdn.com/media/2010/05/Screenshot127.png" width="400" height="333" border="0" /></a>
  </div>
  
  <div style="background-color: white; color: #333333; font-family: Ubuntu, 'Segoe UI', Helvetica, Georgia, sans-serif; font-size: 13px; line-height: 21px; margin-bottom: 10px; margin-top: 10px; padding: 0px; text-align: justify;">
  </div>
</div>