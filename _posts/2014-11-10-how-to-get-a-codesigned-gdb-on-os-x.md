---
id: 493
title: How to get a “codesigned” gdb on OS X?
date: 2014-11-10T11:59:42+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=493
permalink: /?p=493
dsq_thread_id:
  - "6018785878"
categories:
  - "Geek's Stuffs"
---
<p style="text-align: justify;">
  Very interesting problem,  I wanted to run <span style="color: #800000;">gdb</span> on my mac but i was not able to to run it.  Because it was not <span style="color: #800000;">codeSigned</span> . Here&#8217;s the solution.
</p>

<p style="text-align: justify;">
  The Darwin Kernel requires the debugger to have special permissions before it is allowed to control other processes. These permissions are granted by codesigning the GDB executable. Without these permissions, the debugger will report error messages such as:
</p>

<pre class="lang-cpp prettyprint prettyprinted"><code>&lt;span class="typ">Starting&lt;/span>&lt;span class="pln"> program&lt;/span>&lt;span class="pun">:&lt;/span> &lt;span class="pun">/&lt;/span>&lt;span class="pln">x&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">y&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">foo
&lt;/span>&lt;span class="typ">Unable&lt;/span>&lt;span class="pln"> to find &lt;/span>&lt;span class="typ">Mach&lt;/span>&lt;span class="pln"> task port &lt;/span>&lt;span class="kwd">for&lt;/span>&lt;span class="pln"> process&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">id &lt;/span>&lt;span class="lit">28885&lt;/span>&lt;span class="pun">:&lt;/span> &lt;span class="pun">(&lt;/span>&lt;span class="pln">os&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">kern&lt;/span>&lt;span class="pun">)&lt;/span>&lt;span class="pln"> failure &lt;/span>&lt;span class="pun">(&lt;/span>&lt;span class="lit">0x5&lt;/span>&lt;span class="pun">).&lt;/span>
 &lt;span class="pun">(&lt;/span>&lt;span class="pln">please check gdb is codesigned &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln"> see taskgated&lt;/span>&lt;span class="pun">(&lt;/span>&lt;span class="lit">8&lt;/span>&lt;span class="pun">))&lt;/span></code></pre>

<p style="text-align: justify;">
  Codesigning requires a certificate. The following procedure explains how to create one:
</p>

<p style="text-align: justify;">
  <span style="color: #800000;">(Note ) : I tried many times creating certificate for gdb, basic problem was while creating certificate, Please Create certificate for &#8220;System&#8221; not for &#8220;login&#8221; that is main problem. </span>
</p>

<ul style="text-align: justify;">
  <li>
    Start the Keychain Access application (in /Applications/Utilities/Keychain Access.app)
  </li>
  <li>
    Select the Keychain Access -> Certificate Assistant -> Create a Certificate&#8230; menu
  </li>
  <li>
    Then: <ul>
      <li>
        Choose a name for the new certificate (this procedure will use &#8220;gdb-cert&#8221; as an example)
      </li>
      <li>
        Set &#8220;Identity Type&#8221; to &#8220;Self Signed Root&#8221;
      </li>
      <li>
        Set &#8220;Certificate Type&#8221; to &#8220;Code Signing&#8221;
      </li>
      <li>
        Activate the &#8220;Let me override defaults&#8221; option
      </li>
    </ul>
  </li>
  
  <li>
    Click several times on &#8220;Continue&#8221; until the &#8220;Specify a Location For The Certificate&#8221; screen appears, then set &#8220;Keychain&#8221; to &#8220;System&#8221;
  </li>
  <li>
    Click on &#8220;Continue&#8221; until the certificate is created
  </li>
  <li>
    Finally, in the view, double-click on the new certificate, and set &#8220;When using this certificate&#8221; to &#8220;Always Trust&#8221;
  </li>
  <li>
    Exit the Keychain Access application and restart the computer (this is unfortunately required)
  </li>
</ul>

<p style="text-align: justify;">
  Once a certificate has been created, the debugger can be codesigned as follow. In a Terminal, run the following command&#8230;
</p>

<pre class="lang-cpp prettyprint prettyprinted"><code>&lt;span class="pln">codesign &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">s  &lt;/span>&lt;span class="str">"gdb-cert"&lt;/span>  &lt;span class="str">&lt;gnat_install_prefix&gt;&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">bin&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">gdb&lt;/span></code></pre>

<p style="text-align: justify;">
  &#8230; where &#8220;gdb-cert&#8221; should be replaced by the actual certificate name chosen above, and should be replaced by the location where you installed GNAT.
</p>