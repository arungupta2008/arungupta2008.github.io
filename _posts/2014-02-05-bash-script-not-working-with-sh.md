---
id: 259
title: Bash script not working with `sh`
date: 2014-02-05T10:54:35+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=259
permalink: /?p=259
dsq_thread_id:
  - "2222975590"
categories:
  - "Geek's Stuffs"
  - Uncategorized
tags:
  - Linux
  - Scripting
  - Shell
---
I was testing a simple script and I was wondering why it works fine when executed from directory: ./test.sh but when I try with &#8220;sh&#8221; command sh test.sh it&#8217;s not working:
  
test.sh: 3: test.sh: [[: not found
  
test.sh: 7: test.sh: [[: not found
  
Script:

<pre>#!/usr/bin/env bash

if [[ $1 = one ]]
        then
        printf "%b" "two\n" &gt;&2
        exit 0
elif [[ $1 = two ]]
then
        printf "%b" "one\n" &gt;&2
        exit 0
else
        printf "%b" "Specify argument: one/two\n"
        exit 1
fi</pre>

I goggled and found this <a href="http://www.faultserver.com/q/answers-bash-script-not-working-with-sh-401106.html" target="_blank">link</a>
  
Summary

sh is a different program than bash.

Detail

The problem is that the Bourne shell (sh) is not the Bourne Again shell (bash). Namely, sh doesn&#8217;t understand the [[ pragma. In fact, it doesn&#8217;t understand [ either. [ is an actual program or link to /bin/test (or /usr/bin/[, /usr/bin/test).

<pre>$ which [
/bin/[
$ ls -lh /bin/[
-r-xr-xr-x  2 root  wheel    42K Feb 29 17:11 /bin/[</pre>

When you execute your script directly through ./test.sh, you&#8217;re calling the script as the first argument to the program specified in the first line. In this case:
  
#!/usr/bin/env bash
  
Often, this is directly the interpreter (/bin/bash, or any number of other script interpreters), but in your case you&#8217;re using env to run a program in a modified environment &#8212; but that follow argument is still bash. Effectively, ./test.sh is bash test.sh.
  
Because sh and bash are different shells with different syntax interpretations, you&#8217;re seeing that error. If you run bash test.sh, you should see what is expected.
  
More info
  
Others have pointed out in comments that /bin/sh can be a link or other shell. Historically, sh was the Bourne shell on the old AT&T Unix, and in my mind the canonical descent. However, that is different in BSD variations and has diverged in other Unix based systems and distributions over time. If you&#8217;re really interested in the inner workings (including how /bin/sh and /bin/bash can be the same program and behave totally differently), read the following:
  
<a href="http://www.faultserver.com/q/answers-bash-script-not-working-with-sh-401106.html" target="_blank">[1]</a> <a href="http://en.wikipedia.org/wiki/Bourne_shell" target="_blank">[2]</a>

As noted: /bin/sh typically (though not always) invokes a POSIX-compliant Bourne shell. Bash is Not Bourne.
  
Bash will attempt to emulate Bourne when invoked as &#8216;sh&#8217; (as when /bin/sh symlinks or links to /bin/bash), or if $POSIXLY_CORRECT is defined in the invoking environment, when invoked with the &#8211;posix invocation option, or when &#8216;set -o posix&#8217; has been executed. This enables testing a Bourne shell script / command for POSIX compliance.
  
Alternately, invoke scripts / test commands with a known POSIX-compliant shell. &#8216;dash&#8217; is close, the Korn shell (ksh) IIRC offers a POSIX compliant option as well.