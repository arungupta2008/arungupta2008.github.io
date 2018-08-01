---
id: 86
title: Timers in NS2
date: 2013-02-23T19:49:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=86
permalink: /?p=86
blogger_blog:
  - arungupta1.blogspot.com
blogger_author:
  - ARUN GUPTA
blogger_permalink:
  - /2013/02/timers-in-ns2.html
dsq_thread_id:
  - "1792071574"
categories:
  - NS2
  - Uncategorized
tags:
  - Coding
  - ns2
  - Timer
---
<p style="text-align: justify;">
  If you are learning ns2, timers are often an obstacle. They concern with the ability of calling classes methods in consequence of an event schedule. The difficult raises when trying to find out in which order methods are called. If timers are involved, you can&#8217;t expect to find nested calls of methods until the one you are interested in. In this section it is explained how to understand this behavior.
</p>

<p style="text-align: justify;">
  A TimeHandler, as name suggests, is an object created to manage time, and is defined in the common/timer-handler(.cc,.h) files of your ns2 distribution. This handler is in charge to schedule the execution of events during the simulation. The time the handler refers to is the simulation time, not depending on the time your machine uses to process the code.<br /> A timer is like a state machine and is charachterized by three states. The first is <code>TIMER_IDLE</code> which means that timer can manage an event. The next state is <code>TIMER_PENDING</code>, describing a status in which the timer is waiting to manage an event, and so it can&#8217;t accept new events. This means that the timer has accepted to manage an event to be scheduled in the future and it is busy, waiting for this event. The last state is <code>TIMER_HANDLING</code> in which the event is processed, calling the <code>expire()</code> function. After processing the event, timer returns in idle state.<br /> In cbr/cbr-module(.cc,.h) of the MIRACLE distribution you can find a simple timer example, exploited to manage CBR packets transmission.<br /> In the header file we define a new TimerHandler object. It is NOT possible to use TimerHandler class as is, because each timer has to handle its events in a particular fashion, which depends on the content of <code>expire()</code> function.
</p>

<pre>/**
 * Timer used by CbrModule to schedule packet transmission
 */
class SendTimer : public TimerHandler
{
public:
  SendTimer(CbrModule *m) : TimerHandler() { module = m; }</pre>

<p style="text-align: justify;">
  protected:<br /> virtual void expire(Event *e);<br /> CbrModule* module;<br /> };
</p>

<p style="text-align: justify;">
  We defined the constructor, the <code>expire()</code> function and a reference to the module the timer refers to.<br /> On the other side, when defining CbrModule, we have to add <code>SendTimer_</code> as a friend class, in order to make it able to properly manage events. In this case <code>expire()</code> function has to call a CbrModule private method to activate packet sending processes.
</p>

<pre>friend class SendTimer;</pre>

<p style="text-align: justify;">
  It is also necessary to define (in CbrModule) the timer itself, to have a reference to the object to whom submit events.
</p>

<pre>SendTimer sendTmr_;  /*timer which schedules packet transmissions*/</pre>

<p style="text-align: justify;">
  In CbrModule.cc file, when you define the module constructor you have also to activate Timer constructor. This one has a reference to <b>this</b> to definitively associate <code>SendTimer</code> to this <code>CbrModule</code>. If you look at the definition of timer constructor, you&#8217;ll see that it only associates a CbrModule to the object (the one which submits events) to be managed by the timer.
</p>

<pre>CbrModule::CbrModule() 
  : sendTmr_(this),</pre>

<p style="text-align: justify;">
  At the top of the same file there is the definition of <code>expire()</code> function. When timer switchs to the <code>TIMER_HANDLING</code> state, it refers to this particular set of actions. When a CbrModule event expires, the function <code>transmit()</code> is called. Note that this function is defined in <code>CbrModule</code>, so Timer class has to be declaredas a friend of Module one. The <code>module</code> attribute refers to <code>CbrModule</code>, as explained before (see the constructor).
</p>

<pre>void SendTimer::expire(Event *e)
{
  module-&gt;transmit();
}</pre>

<p style="text-align: justify;">
  Now we are ready to schedule an event. <code>TimerHandler</code> class offers two methods to do this. They work in a similar fashion: both of them schedule an event but, while one is made to be called occasionally (i.e., when the timer is not busy, <code>TIMER_IDLE</code>), the second is created to work in an always pending status, in order to consecutively recall <code>expire()</code> function. If timer is always in <code>TIMER_PENDING</code> status, no other (sporadic) events can be managed by the timer. The former is called <code>sched()</code> and the latter is called <code>resched()</code>. The <code>sched()</code> function works only if timer is <code>TIMER_IDLE</code> while <code>resched()</code> can potentially cancel a previously scheduled <code>TIMER_PENDING</code> event and to schedule its new event. In this way the timer is maintaned always busy for those methods which don&#8217;t call <code>resched()</code> function. If your method instead, has the privileged <code>resched()</code> call you can access and modify the events.<br /> In <code>CbrModule</code> we want to periodically transmit a packet. To achieve this result we use <code>resched()</code> function.
</p>

<pre>void CbrModule::start()
{
  ...
  sendTmr_.resched(period_);
}</pre>

<p style="text-align: justify;">
  At the end of <code>transmit()</code> method we reschedule again an event in order to create a &#8220;self-updating&#8221; loop. In this case, at the end of expire function, we schedule the timer for next <code>period_</code> instants, maintaining the loop.
</p>

<p style="text-align: justify;">
  Thanx to <a href="http://telecom.dei.unipd.it/ns/miracle/nsmiracle-howto/node6.html" target="_blank">ns-miracles</a> for this post
</p>