---
id: 487
title: Restoring lost commits in git
date: 2014-10-28T19:18:47+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=487
permalink: /?p=487
dsq_thread_id:
  - "6021337897"
categories:
  - "Geek's Stuffs"
tags:
  - Interesting
  - Mac
  - Technical
---
Hey i am writing post after a long time.

I was working in git and committed some changes, i forgot to pushed to branch and i forgot the commit too. I reseted the HEAD :(.

So, you just did a <span style="color: #800000;"><code>git reset --hard HEAD^</code></span> and threw out your last commit. Well, it turns out you really did need those changes. . Don’t fear, git should still have your commit. When you do a reset, the commit you threw out goes to a “dangling” state. It’s still in git’s datastore, waiting for the next garbage collection to clean it up. So unless you’ve ran a <span style="color: #800000;"><code>git gc</code></span> since you tossed it, you should be in the clear to restore it.

<pre>$ git show-ref -h HEAD
  7c61179cbe51c050c5520b4399f7b14eec943754 HEAD

$ git reset --hard HEAD^
  HEAD is now at 39ba87b Fixing about and submit pages so they don't look stupid

$ git show-ref -h HEAD
  39ba87bf28b5bb223feffafb59638f6f46908cac HEAD</pre>

So our <span style="color: #800000;"><code>HEAD</code></span> has been backed up by one commit. At this point if we wanted it back we could just <span style="color: #800000;"><code>git pull</code></span>, but we’re assuming that only our local repository knows about the commit. We need the SHA1 of the commit so we can bring it back. We can prove that git knows about the commit still with the `fsck` command:

<pre>$ git fsck --lost-found
  [... some blobs omitted ...]
  dangling commit 7c61179cbe51c050c5520b4399f7b14eec943754</pre>

You can also see the that git knows about the commit still by using the `reflog`command:

<pre>$ git reflog
  39ba87b... HEAD@{0}: HEAD~1: updating HEAD
  7c61179... HEAD@{1}: pull origin master: Fast forward
  [... lots of other refs ...]
</pre>

So, we now have our SHA1: `7c61179`. If we want to get immediately apply it back onto our current branch, doing a `git merge` will recover the commit:

<pre>$ git merge 7c61179
  Updating 39ba87b..7c61179
  Fast forward
    css/screen.css |    4 ++++
    submit.html    |    4 ++--
    2 files changed, 6 insertions(+), 2 deletions(-)
</pre>

This command will bring your lost changes back and make sure that `HEAD` is pointing at the commit. From here you can continue to work as normal! You could also checkout the SHA1 into a new branch, but really a merge is the fastest and easiest way to restore that lost commit once you have the hash. If you have other ways let us know in the comments!

Thanx to <a href="http://gitready.com/advanced/2009/01/17/restoring-lost-commits.html" target="_blank">gitReady</a> for this valuable post.