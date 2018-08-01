---
id: 326
title: Understanding Xenomai
date: 2014-04-01T18:10:49+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=326
permalink: /?p=326
dsq_thread_id:
  - "2573312962"
categories:
  - Linux
  - Uncategorized
tags:
  - Xenomai
---
<p style="text-align: justify;">
  Before understanding Xenomai it&#8217;s really important to understand the Normal Linux os and Real Time OS and how they execute their instructions.<br /> Definition from Xenomai&#8217;s Website : Xenomai is a real-time development framework cooperating with the Linux kernel, in order to provide a pervasive, interface-agnostic, hard real-time support to user-space applications, seamlessly integrated into the GNU/Linux environment. Xenomai is based on an abstract RTOS core, usable for building any kind of real-time interfaces, over a nucleus which exports a set of generic RTOS services. Any number of RTOS personalities called &#8220;skins&#8221; can then be built over the nucleus, providing their own specific interface to the applications, by using the services of a single generic core to implement it. Xenomai runs over seven architectures (namely ppc, blackfin, arm, x86, x86_64, ia64 and ppc64), a variety of embedded and server platforms, and can be coupled to two major Linux kernel versions (2.4 and 2.6), for MMU-enabled and MMU-less systems. Supported real-time APIs include POSIX 1003.1b, VxWorks, pSOS+, VRTX and uITRON.
</p>

<pre>## Difference between RT os and Normal OS ##</pre>

<p style="text-align: justify;">
  &#8211; The Linux scheduler, like that of other OSes such as Windows or MacOS, is designed for best average response, so it feels fast and interactive even when running many programs. However, it doesn&#8217;t guarantee that any particular task will always run by a given deadline. A task may be suspended for an arbitrarily long time, for example while a Linux device driver services a disk interrupt.
</p>

<p style="text-align: justify;">
  &#8211; Scheduling guarantees are offered by real-time operating systems (RTOSes), such as QNX, LynxOS or VxWorks. RTOSes are typically used for control or communications applications, not for general purpose computing.
</p>

<p style="text-align: justify;">
  &#8211; The general idea of RT Linux is that a small real-time kernel runs beneath Linux, meaning that the real-time kernel has a higher priority than the Linux kernel. Real-time tasks are executed by the real-time kernel, and normal Linux programs are allowed to run when no real-time tasks have to be executed. Linux can be considered as the idle task of the real-time scheduler. When this idle task runs, it executes its own scheduler and schedules the normal Linux processes. Since the real-time kernel has a higher priority, a normal Linux process is preempted when a real-time task becomes ready to run and the real-time task is executed immediately.
</p>

<pre>How is the real-time kernel given higher priority than Linux kernel?</pre>

<p style="text-align: justify;">
  Basically, an operating system is driven by interrupts, which can be considered as the heartbeats of a computer:
</p>

<p style="text-align: justify;">
  1. All programs running in an OS are scheduled by a scheduler which is driven by timer interrupts of a clock to reschedule at certain times.<br /> 2. An executing program can block or voluntary give up the CPU in which case the scheduler is informed by means of a software interrupt (system call).<br /> 3. Hardware can generate interrupts to interrupt the normal scheduled work of the OS for fast handling of hardware.
</p>

<pre>RT Linux uses the flow of interrupts to give the real-time kernel a higher priority than the Linux kernel:</pre>

<p style="text-align: justify;">
  1. When an interrupt arrives, it is first given to the real-time kernel, and not to the Linux kernel. But interrupts are stored to give them later to Linux when the real-time kernel is done.<br /> 2. As first in row, the real-time kernel can run its real-time tasks driven by these interrupts.<br /> 3. Only when the real-time kernel is not running anything, the interrupts which were stored are passed on to the Linux kernel.<br /> 4. As second in row, Linux can schedule its own processes driven by these interrupt.
</p>

<pre>Hence, when a normal Linux program runs and a new interrupt arrives:</pre>

<p style="text-align: justify;">
  1. It is first handled by an interrupt handler set by the real-time kernel;<br /> 2. The code in the interrupt handler awakes a real-time task;<br /> 3. Immediately after the interrupt handler, the real-time scheduler is called ;<br /> 4. The real-time scheduler observes that another real-time task is ready to run, so it puts the Linux kernel to sleep, and awakes the real-time task.<br /> Hence, to the real-time kernel and Linux kernel coexist on a single machine a special way of passing of the interrupts between real-time kernel and the Linux kernel is needed. Each flavor of RT Linux does this is in its own way. Xenomai uses an interrupt pipeline from the [Adeos project][1]. For more information, see also [Life with Adeos][2].<br /> [1]: http://home.gna.org/adeos/<br /> [2]: http://www.xenomai.org/documentation/xenomai-2.3/pdf/Life-with-Adeos-rev-B.pdf
</p>

<h1 style="text-align: justify;">
  Xenomai<br /> &#8212;&#8212;&#8212;&#8211;
</h1>

<p style="text-align: justify;">
  The Xenomai project was launched in August 2001.<br /> Xenomai is based on an abstract RTOS core, usable for building any kind of real-time interfaces, over a nucleus which exports a set of generic RTOS services. Any number of RTOS personalities called “skins” can then be built over the nucleus, providing their own specific interface to the applications, by using the services of a single generic core to implement it.<br /> The following skins on the generic core are implemented :<br /> POSIX<br /> pSOS+<br /> VxWorks<br /> VRTX<br /> native: the Xenomai skin<br /> uITRON<br /> RTAI: only in kernel threads<br /> Xenomai allows to run real-time threads either strictly in kernel space, or within the address space of a Linux process. A real-time task in user space still has the benefit of memory protection, but is scheduled by Xenomai directly, and no longer by the Linux kernel. The worst case scheduling latency of such kind of task is always near to the hardware limits and predictable, since Xenomai is not bound to synchronizing with the Linux kernel activity in such a context, and can preempt any regular Linux activity with no delay. Hence, he preferred execution environment for Xenomai applications is user space context.<br /> But there might be a few cases where running some of the real-time code embodied into kernel modules is required, especially with legacy systems or very low-end platforms with under-performing MMU hardware. For this reason, Xenomai&#8217;s native API provides the same set of real-time services in a seamless manner to applications, regardless of their execution space. Additionally, some applications may need real-time activities in both spaces to cooperate, therefore special care has been taken to allow the latter to work on the exact same set of API objects.<br /> In our terminology, the terms &#8220;thread&#8221; and &#8220;task&#8221; have the same meaning. When talking about a Xenomai task we refer to real-time task in user space, i.e., within the address space of a Linux process, not to be confused with regular Linux task/thread.
</p>