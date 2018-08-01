---
id: 15
title: Constant In C
date: 2012-12-11T17:45:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=15
permalink: /?p=15
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/12/constant-in-c.html
dsq_thread_id:
  - "1941259394"
categories:
  - C or C++
  - Uncategorized
tags:
  - C-Skills
  - Coding
---
<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  A C constant is usually just the written version of a number. For example 1, 0, 5.73, 12.5e9. We can specify our constants in octal or hexadecimal, or force them to be treated as long integers.
</div>

<ul style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: left;">
  <li>
    Octal constants are written with a leading zero &#8211; 015.
  </li>
  <li>
    Hexadecimal constants are written with a leading 0x &#8211; 0x1ae.
  </li>
  <li>
    Long constants are written with a trailing L &#8211; 890L.
  </li>
</ul>

<span style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: left;">Character constants are usually just the character enclosed in single quotes; &#8216;a&#8217;, &#8216;b&#8217;, &#8216;c&#8217;. Some characters can&#8217;t be represented in this way, so we use a 2 character sequence as follows.</span>

<table style="background-color: #f1f1f1; border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; color: black; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; padding-left: 5px; text-align: left; vertical-align: top; width: 553px;">
  <tr>
    <td style="border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; margin-bottom: 0px; vertical-align: top;">
      <pre style="font-family: 'Courier New', monospace;">'\n' newline<br />'\t' tab<br />'\\' backslash<br />'\'' single quote<br />'\0' null ( Usedautomatically to terminate character string )<br /></pre>
    </td>
  </tr>
</table>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  In addition, a required bit pattern can be specified using its octal equivalent.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  &#8216;\044&#8217; produces bit pattern 00100100.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  Character constants are rarely used, since string constants are more convenient. A string constant is surrounded by double quotes eg &#8220;Brian and Dennis&#8221;. The string is actually stored as an array of characters. The null character &#8216;\0&#8217; is automatically placed at the end of such a string to act as a string terminator.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  A character is a different type to a single character string. This is important poing to note.
</div>

<h1 style="background-color: white; font-family: Helvetica, Arial, 'Liberation Sans', FreeSans, sans-serif; font-size: 18px; font-weight: normal; line-height: 1.5; margin-bottom: 0px; text-align: left;">
  Defining Constants
</h1>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  ANSI C allows you to declare <em>constants</em>. When you declare a constant it is a bit like a variable declaration except the value cannot be changed.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  The <i>const</i> keyword is to declare a constant, as shown below:
</div>

<table style="background-color: #f1f1f1; border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; color: black; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; padding-left: 5px; text-align: left; vertical-align: top; width: 553px;">
  <tr>
    <td style="border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; margin-bottom: 0px; vertical-align: top;">
      <pre style="font-family: 'Courier New', monospace;">int const a = 1;<br />const int a =2;<br /></pre>
    </td>
  </tr>
</table>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  <b>Note:</b>
</div>

<ul style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: left;">
  <li>
    You can declare the <i>const</i> before or after the type. Choose one an stick to it.
  </li>
  <li>
    It is usual to initialise a <i>const</i> with a value as it cannot get a value <em>any other way</em>.
  </li>
</ul>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  The preprocessor <i>#define</i> is another more flexible (see Preprocessor Chapters) method to define <em>constants</em> in a program.
</div>

<table style="background-color: #f1f1f1; border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; color: black; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; padding-left: 5px; text-align: left; vertical-align: top; width: 553px;">
  <tr>
    <td style="border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; margin-bottom: 0px; vertical-align: top;">
      <pre style="font-family: 'Courier New', monospace;">#define TRUE  1<br />#define FALSE  0<br />#define NAME_SIZE 20<br /></pre>
    </td>
  </tr>
</table>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  Here TRUE, FALSE and NAME_SIZE are constant
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  You frequently see const declaration in function parameters. This says simply that the function is <b>not</b> going to change the value of the parameter.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  The following function definition used concepts we have not met (see chapters on functions, strings, pointers, and standard libraries) but for completenes of this section it is is included here:
</div>

<table style="background-color: #f1f1f1; border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; color: black; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; padding-left: 5px; text-align: left; vertical-align: top; width: 553px;">
  <tr>
    <td style="border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; margin-bottom: 0px; vertical-align: top;">
      <pre style="font-family: 'Courier New', monospace;">void strcpy(char *buffer, char const *string)<br /></pre>
    </td>
  </tr>
</table>

<h1 style="background-color: white; font-family: Helvetica, Arial, 'Liberation Sans', FreeSans, sans-serif; font-size: 18px; font-weight: normal; line-height: 1.5; margin-bottom: 0px; text-align: left;">
  The enum Data type
</h1>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  <i>enum</i> is the abbreviation for ENUMERATE, and we can use this keyword to declare and initialize a sequence of integer constants. Here&#8217;s an example:
</div>

<table style="background-color: #f1f1f1; border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; color: black; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; padding-left: 5px; text-align: left; vertical-align: top; width: 553px;">
  <tr>
    <td style="border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; margin-bottom: 0px; vertical-align: top;">
      <pre style="font-family: 'Courier New', monospace;">enum colors {RED, YELLOW, GREEN, BLUE};<br /></pre>
    </td>
  </tr>
</table>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  I&#8217;ve made the constant names uppercase, but you can name them which ever way you want.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  Here, <i>colors</i> is the name given to the set of constants &#8211; the name is optional. Now, if you don&#8217;t assign a value to a constant, the default value for the first one in the list &#8211; <i>RED</i> in our case, has the value of <i></i>. The rest of the undefined constants have a value 1 more than the one before, so in our case, <i>YELLOW</i> is <i>1</i>, <i>GREEN</i> is <i>2</i> and <i>BLUE</i> is <i>3</i>.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  But you can assign values if you wanted to:
</div>

<table style="background-color: #f1f1f1; border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; color: black; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; padding-left: 5px; text-align: left; vertical-align: top; width: 553px;">
  <tr>
    <td style="border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; margin-bottom: 0px; vertical-align: top;">
      <pre style="font-family: 'Courier New', monospace;">enum colors {RED=1, YELLOW, GREEN=6, BLUE };<br /></pre>
    </td>
  </tr>
</table>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  Now RED=1, YELLOW=2, GREEN=6 and BLUE=7.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  The main advantage of <i>enum</i> is that if you don&#8217;t initialize your constants, each one would have a unique value. The first would be zero and the rest would then count upwards.
</div>

<div style="background-color: white; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; text-align: justify;">
  You can name your constants in a weird order if you really wanted&#8230;
</div>

<table style="background-color: #f1f1f1; border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; color: black; font-family: verdana, helvetica, arial, sans-serif; font-size: 12px; padding-left: 5px; text-align: left; vertical-align: top; width: 553px;">
  <tr>
    <td style="border-bottom-color: rgb(170, 170, 170); border-bottom-style: solid; border-bottom-width: 1px; border-collapse: collapse; border-image: initial; border-left-color: rgb(170, 170, 170); border-left-style: solid; border-left-width: 1px; border-right-color: rgb(170, 170, 170); border-right-style: solid; border-right-width: 1px; border-top-color: rgb(170, 170, 170); border-top-style: solid; border-top-width: 1px; margin-bottom: 0px; vertical-align: top;">
      <pre style="font-family: 'Courier New', monospace;">#include &lt;stdio.h><br /><br />int main() {<br />  enum {RED=5, YELLOW, GREEN=4, BLUE};<br /><br />  printf("RED = %d\n", RED);<br />  printf("YELLOW = %d\n", YELLOW);<br />  printf("GREEN = %d\n", GREEN);<br />  printf("BLUE = %d\n", BLUE);<br />  return 0;<br />}<br /><br />This will produce following results<br /><br />  RED = 5<br />  YELLOW = 6<br />  GREEN = 4<br />  BLUE = 5</pre>
    </td>
  </tr>
</table>

Copied From <a href="http://www.tutorialspoint.com/ansi_c/c_using_constants.htm" target="_blank">Tutorial C</a>