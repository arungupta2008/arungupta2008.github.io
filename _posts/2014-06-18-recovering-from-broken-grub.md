---
id: 434
title: Recovering from Broken Grub
date: 2014-06-18T00:16:43+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=434
permalink: /?p=434
dsq_thread_id:
  - "2772941737"
categories:
  - "Geek's Stuffs"
tags:
  - Grub
  - Linux
---
<p style="text-align: justify;">
  On Friday, i was trying to down-grade Grub to grub-legacy. So installed grub-legacy, i knew i was playing with bootloader. When i restart my OS, as expected grub was not able to find out the OS. Problem became more worsen when i came to know, i didn&#8217;t installed stage1, stage1.5 and stage2 scripts means i didn&#8217;t ran commands<strong>(grub-mkconfig)</strong>.
</p>

<p style="text-align: justify;">
  Dos grub didn&#8217;t had <strong>grub-install, </strong>
</p>

<div style="width: 746px" class="wp-caption alignnone">
  <img src="http://cdn.ttgtmedia.com/digitalguide/images/Misc/figuur1.gif" alt="" width="736" height="416" />
  
  <p class="wp-caption-text">
    Grub Error
  </p>
</div>

<p style="text-align: justify;">
  So i googled didn&#8217;t found any solution. I read from different blog, websites and tried this.
</p>

<ol style="text-align: justify;">
  <li>
    Use any live os and run <strong>grub-install</strong>
  </li>
</ol>

<pre>First Mount the partition where OS is installed. You can find the partition by running. 

<strong>#$ blkid</strong>
/dev/sda1: UUID="ee51f4e9-1ef8-4b65-8ef4-299600e8cbf4" TYPE="ext4" PTTYPE="dos" PARTUUID="c679c6ed-01" 

/dev/sda2: UUID="cb97ec88-4282-459a-852f-f619138d46d9" TYPE="ext4" PARTUUID="c679c6ed-02"

then run 
<strong>sudo mount /dev/sda1 /mnt</strong> 
(Make sure partition in write mode)
<strong>mount -o remount, rw /dev/sda2
</strong>(Here sdb3 where OS is installed)

<strong>grub-install --target=/mnt --recheck /dev/sda2</strong></pre>

<p style="text-align: justify;">
  Now Scripts are installed reboot the machine.(Most probably you will get a grub black screen)
</p>

<p style="text-align: justify;">
  Now you have to do 3 things
</p>

<p style="text-align: justify;">
  <strong><span style="color: #000080;">a. Find the partitions. </span></strong>
</p>

<pre style="text-align: justify;">ls</pre>

<p style="text-align: justify;">
  it will show you how many partitions are here,  here you may get like
</p>

    (hd0) (hd0,5) (hd0,1) (hd1) (hd1,1) (hd1,2) (fd0) (hd0,msdos1) (hd0, msdos2)

<p style="text-align: justify;">
  Then run
</p>

<pre style="text-align: justify;">ls /(hd0,0)</pre>

<p style="text-align: justify;">
  and observe the output, if you are getting Linux root(where folders like etc, boot are present) then this is your root.
</p>

<p style="text-align: justify;">
  <strong><span style="color: #000080;">b. Set the root</span></strong>
</p>

<pre>root (hd0,0)</pre>

<p style="text-align: justify;">
  Here (hd0,0) Explained Here.
</p>

<ul style="text-align: justify;">
  <li>
    The brackets are a must; all devices listed in GRUB menu must be enclosed in brackets.
  </li>
  <li>
    hd stands for hard disk; alternatively, fd stands for floppy disk, cd stands for CD-ROM etc.
  </li>
  <li>
    The first number (integer for geeks) refers to the physical hard drive number; in this case, the first drive, as they are counted from zero up. For example, hd2 refers to the third physical hard drive.
  </li>
  <li>
    The second number refers to the partition number of the selected hard drive; again, partitions are counted from zero up. In this case, 1 stands for the second partition.
  </li>
</ul>

<p style="text-align: justify;">
  From here, it is evident that GRUB (menu) does not discriminate between IDE or SCSI drives or primary or logical partitions. The task of deciding which hard drive or partition may boot is left to BIOS and Stage 1. As you see, the notation is very simple.
</p>

<p style="text-align: justify;">
  Primary partitions are marked from 0 to 3 (hd?,0), (hd?,1), (hd?,2), (hd?,3). Logical partitions in the extended partition are counted from 4 up, regardless of the actual number of primary partitions on the hard disk, e.g. (hd1,7).
</p>

<p style="text-align: justify;">
  <em><strong><span style="color: #800000;">For me I guessed, i tried like setting up the root, like above mentioned then. used grub&#8217;s ls command if ls /boot+tab shows any thing that partition where you have to install actually re-install your Grub. </span></strong></em>
</p>

<p style="text-align: justify;">
  <strong><span style="color: #000080;">c. Load the kernel</span></strong>
</p>

<pre>kernel /boot/vmlinux-linux  ro root=/dev/sda2</pre>

<p style="text-align: justify;">
  <strong><span style="color: #000080;">d. Load the Linux img</span></strong>
</p>

<pre>initrd /boot/vmlinux-linux-lts.img</pre>

<p style="text-align: justify;">
  Then Run
</p>

<pre>boot</pre>

<p style="text-align: justify;">
  You will be able to boot the desired OS. <a href="http://www.gnu.org/software/grub/manual/legacy/Installing-GRUB-natively.html" target="_blank">[1]</a>
</p>