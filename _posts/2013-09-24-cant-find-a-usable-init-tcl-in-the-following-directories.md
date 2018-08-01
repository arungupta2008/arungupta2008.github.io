---
id: 164
title: 'Can&#8217;t find a usable init.tcl in the following directories'
date: 2013-09-24T13:51:42+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=164
permalink: /?p=164
dsq_thread_id:
  - "1792639007"
categories:
  - NS2
  - Uncategorized
tags:
  - Coding
  - ns2
---
_sometimes while installing ns2  this error &#8220;application-specific initialization failed: Can&#8217;t find a usable init.tcl in the following directories: &#8221; sucks , we don&#8217;t know what to do._

 _I have a solution._

_application-specific initialization failed: Can&#8217;t find a usable init.tcl in the following directories:/root/ns2/ns-allinone-2.34/lib/tcl8.4 /usr/local/lib/tcl8.4 /usr/lib/tcl8.4 /usr/local/library /usr/library /usr/tcl8.4.18/library /tcl8.4.18/library /root/ns2/ns-allinone-2.34/lib/tcl8.4_

_or at local folder too _

_There are some solution please try may be they can help:_

<em id="__mceDel">Solution 1:<br /> 1) Go to location root-usr-local-bin by giving following command in terminal<br /> cd /usr/local/bin<br /> 2) There you would find the ns file. We just need to remove it by giving following command<br /> rm ns<br /> 3) Thats it, you are done. Now your ns starts running successfully.</em>

_Solution 2:_

_ This error can happen if you make any changes to the &#8220;ns-allinone-2.34/&#8221; directory :_
  
_Renaming the directory, moving the directory to another location,_
  
_i.e. anything that will change the &#8220;/home/arungupta2008/ns-allinone-2.34/tcl8.4.18/lib/&#8221; path._
  
_Or when changes were made in /home/arungupta2008/ns-allinone-2.34/tcl8.4.18/**lib/**_
  
_Note : _
  
_The binary &#8216;ns&#8217; is hard coded to know the location of it&#8217;s libraries, tclsh8* :_
  
_/home/arungupta2008/ns-allinone-2.34/tcl8.4.18/**bin/**, /home/arungupta2008/ns-allinone-2.34/tcl8.4.18/**lib/**_

_Workarounds, fixes : _
  
_1) cd ns-allinone-2.34/tcl8.4.18/ && ln -s lib/ library_
  
_2) Reinstall ns-allinone-2.34  2. The problem is because, ns executable is also at /usr which is conflicting._

&nbsp;

Note : while removing symlinks first make that file removable then , you can remove that file  for Ex.     chmod 755 ns