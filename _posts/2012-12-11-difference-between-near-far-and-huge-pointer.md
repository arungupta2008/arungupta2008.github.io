---
id: 16
title: Difference between Near , Far and Huge Pointer
date: 2012-12-11T17:16:00+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=16
permalink: /?p=16
blogger_blog:
  - arungupta1.blogspot.com
blogger_permalink:
  - /2012/12/difference-between-near-far-and-huge.html
dsq_thread_id:
  - "1768719824"
categories:
  - C or C++
tags:
  - C-Skills
  - Coding
---
<span style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">as we know by default the pointers are near for example <b>int *p</b> is a near pointer&#8230; size of near pointer is 2 bytes in case of 16 bit compiler&#8230;&#8230;.. n we already know very well size varies compiler to compiler&#8230;&#8230; <span><span style="color: black;">They only store the offset of the address the pointer is referencing. </span></span><span><span style="color: black;">. An address consisting of only an offset has a range of 0 &#8211; 64K bytes&#8230;. i think there is no need to discuss near pointers anymore&#8230;. so come to the main point&#8230;.. that is far and huge pointers&#8230;&#8230;</span></span></span>

<div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
  <span><span style="color: black;"><br /></span></span>
</div>

<div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
  <span><span style="color: black;"><b>far and huge pointers:</b></span></span>
</div>

<div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
  <span><span style="color: black;">Far and huge pointers have a size of 4 bytes. They store both the segment and the offset of the address the pointer is referencing. thn what is the difference between them &#8230;&#8230;&#8230;..</span></span>
</div>

<div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
  <span></p> 
  
  <div style="text-align: justify;">
    <b>Limitation of far pointer:</b>
  </div>
  
  <div style="color: #666666; text-align: justify;">
    <b><span style="color: maroon;"></span></b><span style="color: black;">We cannot change or modify the segment address of given far address by applying any arithmetic operation on it. That is by using arithmetic operator we cannot jump from one segment to other segment. If you will increment the far address beyond the maximum value of its offset address instead of incrementing segment address it will repeat its offset address in cyclic order.</span><span style="color: black; line-height: normal;"> this is also called wrapping&#8230;..i.e. if offset is 0xffff and we add 1 then it is 0x0000 and similarly if we decrease 0x0000 by 1 then it is 0xffff and remember there is no change in the segment&#8230;.</span>
  </div>
  
  <p>
    </span></div> 
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">Now i am going to <b>compare huge and far pointers&#8230;&#8230;&#8230;.</b></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><b><br /></b></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">1.</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><span><b>When a far pointer is incremented or decremented ONLY the offset of the pointer is actually incremented or decremented but in case of huge pointer both segment and offset value will change&#8230;..</b></span></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><span><b>like if we have</b></span></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><br /></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">int main()</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">{</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">char far* f=(char far*)0x0000ffff;</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">printf(&#8220;%Fp&#8221;,f+0x1);</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">return 0;</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">}</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><br /></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">then the output is:</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">0000:0000</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><br /></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;">as we see there is no change in segment value&#8230;&#8230;.</span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><br /></span></span>
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      and in case of huge&#8230;&#8230;..
    </div>
    
    <div style="background-color: white; color: #222222; font-family: Arial, Tahoma, Helvetica, FreeSans, sans-serif; font-size: 13px; line-height: 18px;">
      <span><span style="color: black;"><span></p> 
      
      <div>
        <div>
          <span><span><br /></span></span>
        </div>
        
        <div>
          <span><span>int main()</span></span>
        </div>
        
        <div>
          <span><span>{</span></span>
        </div>
        
        <div>
          <span><span>char huge* h=(char huge*)0x0000000f;</span></span>
        </div>
        
        <div>
          <span><span>printf(&#8220;%Fp&#8221;,h+0x1);</span></span>
        </div>
        
        <div>
          <span><span>return 0;</span></span>
        </div>
        
        <div>
          <span><span>}</span></span>
        </div>
        
        <div>
        </div>
      </div>
      
      <div>
        <span><span>then the o/p is:</span></span>
      </div>
      
      <div>
        <span><span>0001:0000</span></span>
      </div>
      
      <div>
        <span><span><br /></span></span>
      </div>
      
      <div>
        <span><span>it shows bcoz of increment operation not only offset value but segment value also change&#8230;&#8230;&#8230;. that means segment will not change in case of far pointers but in case of huge it can move from one segment to another &#8230;&#8230;</span></span>
      </div>
      
      <div>
      </div>
      
      <div>
        2.
      </div>
      
      <div>
        <span><b>When relational operators are used on far pointers only the offsets are compared.In other words relational operators will only work on far pointers if the segment values of the pointers being compared are the same. and in case of huge this will not happen, actually comparison of absolute addresses takes place&#8230;..</b>. lets understand with the help of an example&#8230;</span>
      </div>
      
      <div>
        <span>in far&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;.</span>
      </div>
      
      <div>
        <span><br /></span>
      </div>
      
      <div>
        <span>int main()</span>
      </div>
      
      <div>
        <span>{</span>
      </div>
      
      <div>
        <span>char far * p=(char far*)0x12340001;</span>
      </div>
      
      <div>
        <span>char far* p1=(char far*)0x12300041;</span>
      </div>
      
      <div>
        <span>if(p==p1)</span>
      </div>
      
      <div>
        <span>printf(&#8220;same&#8221;);</span>
      </div>
      
      <div>
        <span>else</span>
      </div>
      
      <div>
        <span>printf(&#8220;different&#8221;);</span>
      </div>
      
      <div>
        <span>return 0;</span>
      </div>
      
      <div>
        <span>}</span>
      </div>
      
      <div>
        <span><br /></span>
      </div>
      
      <div>
        <span>Output:</span>
      </div>
      
      <div>
        <span>different</span>
      </div>
      
      <div>
      </div>
      
      <div>
        in huge&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;..
      </div>
      
      <div>
      </div>
      
      <div>
        <span></p> 
        
        <div>
          <span>int main()</span>
        </div>
        
        <div>
          <span>{</span>
        </div>
        
        <div>
          <span>char huge * p=(char huge*)0x12340001;</span>
        </div>
        
        <div>
          <span>char huge* p1=(char huge*)0x12300041;</span>
        </div>
        
        <div>
          <span>if(p==p1)</span>
        </div>
        
        <div>
          <span>printf(&#8220;same&#8221;);</span>
        </div>
        
        <div>
          <span>else</span>
        </div>
        
        <div>
          <span>printf(&#8220;different&#8221;);</span>
        </div>
        
        <div>
          <span>return 0;</span>
        </div>
        
        <div>
          <span>}</span>
        </div>
        
        <p>
          </span></div> 
          
          <div>
            <span><br /></span>
          </div>
          
          <div>
            <span>Output:</span>
          </div>
          
          <div>
            <span>same</span>
          </div>
          
          <div>
          </div>
          
          <div>
            <span></p> 
            
            <div>
              <span>Explanation:</span>
            </div>
            
            <div>
              <span>as we see the absolute address for both p and p1 is 12341 (1234*10+1 or 1230*10+41) but they are not considered equal in 1st case becoz in case of far pointers only offsets are compared i.e. it will check whether 0001==0041&#8230;. that we know is false&#8230;. and know see what will happen in case of huge&#8230;..</span>the comparison operation is performed on absolute addresses that are equal as i already told&#8230;&#8230;
            </div>
            
            <div>
            </div>
            
            <div>
              3.
            </div>
            
            <div>
              <b>A far pointer is never noramlized but a huge pointer is normalized . A normalized pointer is one that has as much of the address as possible in the segment, meaning that the offset is never larger than 15.</b>
            </div>
            
            <div>
              suppose if we have 0x1234:1234 then the normalized form of it is 0x1357:0004(absolute address is 13574)&#8230;&#8230;.
            </div>
            
            <div>
              <b>A huge pointer is normalized only when some arithmetic operation is performed on it &#8230; and not noramlized during assignment&#8230;.</b>
            </div>
            
            <div>
            </div>
            
            <div>
              int main()
            </div>
            
            <div>
              {
            </div>
            
            <div>
              char huge* h=(char huge*)0x12341234;
            </div>
            
            <div>
              char huge* h1=(char huge*)0x12341234;
            </div>
            
            <div>
              printf(&#8220;h=%Fp\nh1=%Fp&#8221;,h,h1+0x1);
            </div>
            
            <div>
              return 0;
            </div>
            
            <div>
              }
            </div>
            
            <div>
            </div>
            
            <div>
              Output:
            </div>
            
            <div>
              h=1234:1234
            </div>
            
            <div>
              h1=1357:0005
            </div>
            
            <div>
            </div>
            
            <div>
              Explanation:
            </div>
            
            <div>
              as i said above huge is not normalized in case of assignment&#8230;&#8230;but if an arithmetic operation is performed on it &#8230;.. it will be normalized&#8230;. so h is 1234:1234 and h1 is 1357:0005&#8230;&#8230;&#8230;.that is normalized&#8230;&#8230;.
            </div>
            
            <div>
            </div>
            
            <div>
              <div>
                <span><span>4.</span></span>
              </div>
              
              <div>
                <b>The offset of huge pointer is less than 16 because of normalization and not so in case of far pointers&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;.</b>
              </div>
              
              <div>
              </div>
              
              <div>
                lets take an example to understand what i want to say&#8230;..
              </div>
              
              <div>
                int main()
              </div>
              
              <div>
                <div>
                  <span><span>{</span></span>
                </div>
                
                <div>
                  <span><span>char far* f=(char far*)0x0000000f;</span></span>
                </div>
                
                <div>
                  <span><span>printf(&#8220;%Fp&#8221;,f+0x1);</span></span>
                </div>
                
                <div>
                  <span><span>return 0;</span></span>
                </div>
                
                <div>
                  <span><span>}</span></span>
                </div>
              </div>
              
              <div>
              </div>
              
              <div>
                Output:
              </div>
              
              <div>
                0000:0010
              </div>
              
              <div>
              </div>
              
              <div>
                in case of huge
              </div>
              
              <div>
                <div>
                  <span><span>int main()</span></span>
                </div>
                
                <div>
                  <span><span>{</span></span>
                </div>
                
                <div>
                  <span><span>char huge* h=(char huge*)0x0000000f;</span></span>
                </div>
                
                <div>
                  <span><span>printf(&#8220;%Fp&#8221;,h+0x1);</span></span>
                </div>
                
                <div>
                  <span><span>return 0;</span></span>
                </div>
                
                <div>
                  <span><span>}</span></span>
                </div>
                
                <div>
                  <span><span><br /></span></span>
                </div>
                
                <div>
                  <span><span></p> 
                  
                  <div>
                    Output:
                  </div>
                  
                  <div>
                    0001:0000
                  </div>
                  
                  <div>
                  </div>
                  
                  <div>
                    Explanation:
                  </div>
                  
                  <div>
                    as we increment far pointer by 1 it will be 0000:0010&#8230;&#8230; and as we increment huge pointer by 1 thn it will be 0001:0000 bcoz its offset cant be greater than 15 in other words it will be normalized&#8230;&#8230;&#8230;&#8230;
                  </div>
                  
                  <div>
                  </div>
                  
                  <div>
                  </div>
                  
                  <div>
                    Copied from <a href="http://clanguagestuff.blogspot.in/2011/03/difference-between-far-and-huge.html" target="_blank">C Stuff</a> 
                  </div>
                  
                  <p>
                    </span></span></div> </div> </div> 
                    
                    <p>
                      </span></div> 
                      
                      <p>
                        </span></span></span></div>