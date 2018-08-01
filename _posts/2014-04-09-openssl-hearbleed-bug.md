---
id: 340
title: 'OpenSSL &#8220;HeartBleed&#8221; Bug'
date: 2014-04-09T14:51:06+00:00
author: Arun
layout: post
guid: http://arungupta.co.in/blog/?p=340
permalink: /?p=340
dsq_thread_id:
  - "2598161140"
categories:
  - Uncategorized
tags:
  - BUG
  - HeartBeat
  - Linux
  - OpenSSL
---
<p style="text-align: justify;">
                            <img class="alignnone" alt="" src="http://heartbleed.com/heartbleed.png" width="341" height="413" />
</p>

<p style="text-align: justify;">
  Monday afternoon, the IT world got a very nasty wakeup call, <a href="https://www.openssl.org/news/secadv_20140407.txt" target="new">an emergency security advisory</a> from the OpenSSL project warning about <a href="http://heartbleed.com/" target="new">an open bug called &#8220;Heartbleed.&#8221;</a> The bug could be used to pull a chunk of working memory from any server running their current software. There was an emergency patch, but until it was installed, tens of millions of servers were exposed. Anyone running a server was suddenly in crisis mode.
</p>

<p style="text-align: justify;">
  If the &#8220;Heartbleed&#8221; name sounds dramatic, this bug seems to live up to the hype. It’s already far worse than the GoToFail bug that embarrassed Apple <a href="http://www.theverge.com/2014/2/24/5442576/inside-apples-epic-security-flaw">earlier this year</a>, both by the scale of computers affected and the depth of the breach. The new bug would let attackers pull the private keys to the server, letting attackers listen in on data traffic and potentially masquerade as the server. Even worse, it’s old: the bug dates back two years, and it&#8217;s still unclear how long anyone&#8217;s known about it.
</p>

<p style="text-align: justify;">
  OpenSSL isn&#8217;t widely known outside of the coding world, but as many as two out of three servers on the web rely on its software. The sudden reveal means anyone involved is now scrambling for a fix. Already, Yahoo has been exposed by the bug, and experts have advised any Yahoo users to steer clear of their accounts until the company has time to update their servers. (A Yahoo representative tells <em>The Verge </em>the core sites are now patched, although the team is still working to implement the fix across the rest of the site.) Dozens of other smaller companies have also<a href="https://github.com/musalbas/heartbleed-masstest/blob/master/top1000.txt" target="_blank"> reportedly been affected,</a> including Imgur, Flickr, and LastPass (although <a href="http://blog.lastpass.com/2014/04/lastpass-and-heartbleed-bug.html" target="_blank">LastPass says</a> no unencrypted data was exposed). &#8220;It is catastrophically bad, just a hugely damaging bug,&#8221; says ICSI security researcher Nicholas Weaver.
</p>

<p style="text-align: justify;">
  Discovered by Google researcher Neel Mehta, the bug allows an attacker to pull 64k at random from a given server&#8217;s working memory. It&#8217;s a bit like fishing — attackers don&#8217;t know what usable data will be in the haul — but since it can be performed over and over again, there&#8217;s the potential for a lot of sensitive data to be exposed. The server&#8217;s private encryption keys are a particular target, since they&#8217;re necessarily kept in working memory and are easily identifiable among the data. That would allow attackers to eavesdrop on traffic to and from the service, and potentially decrypt any past traffic that had been stored in encrypted form.
</p>

<p style="text-align: justify;">
  For most privacy tools relying on OpenSSL, the takeaway is catastrophic. <a href="https://blog.torproject.org/blog/openssl-bug-cve-2014-0160" target="_blank">A blog post from the Tor Project</a> told users, &#8220;if you need strong anonymity or privacy on the internet, you might want to stay away from the internet entirely for the next few days while things settle.&#8221; In many cases, a few days may not be enough. It will give services time to patch their servers, but if any private keys were compromised before the patch went up, it would give attackers free rein in the months to come. Servers can reset their certificates, but it&#8217;s slow and expensive, and experts suspect many of them may simply assume the patch is enough. &#8220;I bet that there will be a lot of vulnerable servers a year from now,&#8221; Weaver says. &#8220;This won&#8217;t get fixed.&#8221;
</p>

<p style="text-align: justify;">
  Apple, Google and Microsoft appear to be unaffected, along with the major e-banking services. Yahoo, on the other hand, was affected and <a href="https://twitter.com/scottgal/status/453520554407239680" target="new">leaking user credentials</a> for a significant portion of the day before its core sites were fixed. More generally, any server running OpenSSL on Apache or Nginx will be affected, which implicates a huge variety of everyday websites and services.
</p>

<p style="text-align: justify;">
  For now, there are a few ways users can tell which services are safe — but the news isn&#8217;t reassuring. <a href="http://filippo.io/Heartbleed/" target="new">This site</a>, built by developer Filippo Valsorda, offers a spot-check as to which services are currently unpatched, but the site&#8217;s code is also producing false negatives, so it shouldn&#8217;t be taken as definitively ruling anything out. Any patched server will also need to generate new SSL certificates to make sure attackers can&#8217;t use keys that were exposed in the breach. To check, use an SSL tracker <a href="https://sslcheck.globalsign.com/en_US" target="new">like this one</a> and look for a certificate&#8217;s &#8220;issued on&#8221; date, which should be dated after the recent patch. Resetting the certificates will take time and money, but if a compromised site keeps using a compromised certificate, they&#8217;ll be leaving themselves open to an attack.
</p>

<p id="paragraph12" style="text-align: justify;">
  It’s still early to tell what larger changes will be made as a result of the breach, but some lessons are already clear. Despite the vast infrastructure relying on OpenSSL, the open-source project is comparatively underfunded, and some experts have already <a href="https://twitter.com/matthew_d_green/status/453501176336896000" target="new">called for more donations</a> to the project to prevent vulnerabilities like Heartbleed from slipping through the cracks. Perfect Forward Secrecy could also have limited the damage from the bug, preventing decryption after the fact.
</p>

<p id="paragraph13" style="text-align: justify;">
  But the most troubling lesson might be how hard vulnerabilities are to discover, and how damaging they can be once fully revealed. &#8220;These are really subtle bugs,&#8221; Weaver says. &#8220;You might detect it if you ran it through a memory checker, but this is not the kind of thing that just shows up looking at the code.&#8221; That’s a credit to Google, who was rigorous enough to discover the bug — but for anyone relying on secure software, it’s a troubling thought.
</p>

<p style="text-align: justify;">
  Some Comments about clarification of the posts.
</p>

<ul style="text-align: justify;">
  <li>
    The answer to this question is “maybe”. The article here has several points wrong, one of them being that the attacker cannot select which data they are going to have leak. The flaw basically blows out a memory register and returns whatever data happens to be in the extra bytes. It could be something, or, in most cases, it could be nothing. To get useful data, you would have to flood the server with TLS “heartbeat” requests.
  </li>
  <li>
    As someone familiar with this tech, I’d say the author of this article did a decent job covering the main bases. The possibilities are huge. Getting a 64k chunk of random memory is pretty significant. There are just over 262,000 64k chunks in a 16GB server. An attacker can muster 262,000 requests in just a few minutes. Once the random jabs have shaken loose pretty much all the contents of the server’s memory, then the attacker can sift through the responses for the private SSL keys. The private SSL keys can be used by the attacker to imitate the host to visiting browsers, which will then submit login info. Having the server’s private SSL key can also greatly simplify a Man-in-the-middle attack on sessions that are supposed to be private between the browser and the server. Finally, the private SSL key also enables previously-captured network traffic to be fully decrypted.
  </li>
  <li>
    The article is confusing about what the potential leakage is. There is the potential that an attacker could get any kind of data that was loaded into memory, which makes the bug nasty. But it’s not like an attacker could just hit the server and pull everything in memory, or download a specific kind of data. They would have to send millions of heartbeat requests just to guarantee that they got any useful data. And it still wouldn’t be guaranteed.I’m not trying to downplay the seriousness of the issue, but it’s probably not likely that people need to freak out about all their data being stolen right now. The serious concern is the loss of server private keys, so people should go through the process of updating their servers and re-keying their SSL certificates to ensure that they are safe.
  </li>
  <li>
    No it doesn’t; it allows an attacker to see the contents of a small portion of RAM immediately following a chunk of RAM that OpenSSL uses. They have no control over what specific portion of memory it is nor what it contains; it could be anything and what it is exactly really depends on a bunch of pretty much random factors.The concern is that there is a possibility that it could contain something important (like the servers private encryption keys) which would obviously be a problem. This is where the verge article delves into sensationalist BS however they can’t write software that is essentially “push button to steal certs” this would take time and resources to exploit in any meaningful way unless the attacker was very lucky. Again, this is basically like trying to steal someone’s password by walking behind their desk hoping that they happen to be typing it in as you walk by.It’s a big deal because relying on someone not getting lucky is not a good form of security, the chances that this was exploited in a meaningful way is almost nil.
  </li>
</ul>

<p style="text-align: justify;">
  All technical knowledge about Open Ssl 1.0.1
</p>

<p style="text-align: justify;">
  An information disclosure vulnerability has been found, and <a href="http://www.openssl.org/news/secadv_20140407.txt" rel="nofollow">promptly patched</a>, in OpenSSL.
</p>

<p style="text-align: justify;">
  OpenSSL is a very widely used encryption library, responsible for putting the S in HTTPS, and the padlock in the address bar, for many websites.
</p>

<p style="text-align: justify;">
  The bug only exists in the OpenSSL 1.0.1 source code (from version 1.0.1 to 1.0.1f inclusive), because the faulty code relates to a fairly new feature known as the <em>TLS Heartbeat Extension</em>.
</p>

<p style="text-align: justify;">
  The heartbeat extension was first documented in <a href="https://tools.ietf.org/html/rfc6520">RFC 6520</a> in February 2012.
</p>

<p style="text-align: justify;">
  TLS heartbeats are used as &#8220;keep alive&#8221; packets so that the ends of an encrypted connection can agree to keep the session open even when they don&#8217;t have any official data to exchange.
</p>

<p style="text-align: justify;">
  Because the heartbeats consist of a reply and a matching response, they allow either end to confirm not only that the session is open, but also that end-to-end connectivity is working properly.
</p>

<h4 style="text-align: justify;">
  Sending heartbeat requests
</h4>

<p style="text-align: justify;">
  The RFC 6520 standard explicitly restricts the maxium size of a heartbeat request to 214 bytes (16KBytes), but OpenSSL itself generates far shorter requests.
</p>

<p style="text-align: justify;">
  Don&#8217;t worry if you don&#8217;t understand C; but if you do, the OpenSSL heartbeat request code looks like this:
</p>

<pre class="brush: cpp; title: ; notranslate" title="">unsigned int payload = 18; /* Sequence number + random bytes */
unsigned int padding = 16; /* Use minimum padding */

/* Check if padding is too long, payload and padding
* must not exceed 2^14 - 3 = 16381 bytes in total.
*/

OPENSSL_assert(payload + padding &lt;= 16381);

/* Create HeartBeat message, we just use a sequence number
 * as payload to distuingish different messages and add
 * some random stuff.
 *  - Message Type, 1 byte
 *  - Payload Length, 2 bytes (unsigned int)
 *  - Payload, the sequence number (2 bytes uint)
 *  - Payload, random bytes (16 bytes uint)
 *  - Padding
 */

buf = OPENSSL_malloc(1 + 2 + payload + padding);
p = buf;
/* Message Type */
*p++ = TLS1_HB_REQUEST;
/* Payload length (18 bytes here) */
s2n(payload, p);
/* Sequence number */
s2n(s-&gt;tlsext_hb_seq, p);
/* 16 random bytes */
RAND_pseudo_bytes(p, 16);
p += 16;
/* Random padding */
RAND_pseudo_bytes(p, padding);

ret = dtls1_write_bytes(s, TLS1_RT_HEARTBEAT, buf, 3 + payload + padding);
</pre>

<p style="text-align: justify;">
  The reason that the code says that &#8220;payload and padding must not exceed 16381 bytes in total&#8221; is that the 16KByte (16384 byte) maximum heartbeat request size includes one byte to signal that this is a<tt> TLS1_HB_REQUEST</tt>, and two bytes to denote the length of the payload data in the request.
</p>

<p style="text-align: justify;">
  As the code stands, the<tt> OPENSSL_assert </tt>to verify that<tt> payload + padding <= 16381 </tt>is redundant, because the payload size is hard-wired to 18 bytes and the padding size to 16.
</p>

<p style="text-align: justify;">
  But the programmer has tried to do the right thing: put in the check anyway, in case someone changes those payload or padding sizes in the future without considering the consequences.
</p>

<p style="text-align: justify;">
  The code then transmits a heartbeat request consisting of:
</p>

<ul style="text-align: justify;">
  <li>
    The single byte 0x01 (denoting that this is a<tt> TLS1_HB_REQUEST</tt>).
  </li>
  <li>
    Two bytes containing the 16-bit representation of 34 (size of payload plus padding).
  </li>
  <li>
    Two bytes of payload consising of a 16-bit sequence number.
  </li>
  <li>
    16 bytes of random data making up the rest of the 18-byte payload.
  </li>
  <li>
    16 further random padding bytes, required by the standard.
  </li>
</ul>

<h4 style="text-align: justify;">
  Replying to heartbeat requests
</h4>

<p style="text-align: justify;">
  When vulnerable versions of OpenSSL 1.0.1 respond to a heartbeat request, they aren&#8217;t quite so careful in processing the received data.
</p>

<p style="text-align: justify;">
  Heartbeat replies are supposed to contain a copy of the payload data from the request, as a way of verifying that the encrypted circuit is still working both ways.
</p>

<p style="text-align: justify;">
  It turns out that you can send a small heartbeat request, but sneakily set your payload length field to 0xFFFF (65535 bytes).
</p>

<p style="text-align: justify;">
  Then, OpenSSL will uncomplainingly copy 65535 bytes from your request packet, even though you didn&#8217;t send across that many bytes:
</p>

<pre class="brush: cpp; title: ; notranslate" title="">/* Allocate memory for the response, size is 1 byte
 * message type, plus 2 bytes payload length, plus
 * payload, plus padding
 */
buffer = OPENSSL_malloc(1 + 2 + payload + padding);
bp = buffer;

/* Enter response type, length and copy payload */
*bp++ = TLS1_HB_RESPONSE;
s2n(payload, bp);
memcpy(bp, pl, payload);
bp += payload;
/* Random padding */
RAND_pseudo_bytes(bp, padding);

r = dtls1_write_bytes(s, TLS1_RT_HEARTBEAT, buffer, 3 + payload + padding);
</pre>

<p style="text-align: justify;">
  That means OpenSSL runs off the end of your data and scoops up whatever else is next to it in memory at the other end of the connection, for a potential data leakage of approximately 64KB each time you send a malformed heartbeat request.
</p>

<p style="text-align: justify;">
  This bug has been rather melodramatically named &#8220;heartbleed,&#8221; for reasons that should now be obvious.
</p>

<p style="text-align: justify;">
  According to the Finnish National Cyber Security Centre, the sort of data that &#8220;bleeds&#8221; when the bug is triggered varies enormously, but <a href="https://www.cert.fi/en/reports/2014/vulnerability788210.html" rel="nofollow">may include</a>message contents, user credentials, session keys and even copies of a server&#8217;s own private keys.
</p>

<p style="text-align: justify;">
  That&#8217;s not good!
</p>

<h4 style="text-align: justify;">
  Fixing the problem
</h4>

<p style="text-align: justify;">
  Fortunately, there&#8217;s a fix already: simply upgrade to OpenSSL 1.0.1g.
</p>

<p style="text-align: justify;">
  If you don&#8217;t want to or can&#8217;t do that, you can rebuild your current version of OpenSSL from source without TLS Heartbeat support, by adding<tt> -DOPENSSL_NO_HEARTBEATS </tt>at compile time.
</p>

<p style="text-align: justify;">
  Both of these immunise you from this flaw.
</p>

<p style="text-align: justify;">
  The new OpenSSL version includes a bounds check to make sure the payload length you specified isn&#8217;t longer that the data you actually sent:
</p>

<pre class="brush: cpp; title: ; notranslate" title="">/* Read type and payload length first */
if (1 + 2 + 16 &gt; s-&gt;s3-&gt;rrec.length)
        return 0; /* silently discard */
hbtype = *p++;
n2s(p, payload);
if (1 + 2 + payload + 16 &gt; s-&gt;s3-&gt;rrec.length)
        return 0; /* silently discard per RFC 6520 sec. 4 */
</pre>

<p style="text-align: justify;">
  The <tt>-DOPENSSL_NO_HEARTBEATS </tt>compile-time option simply omits the buggy code altogether from vulnerable versions.
</p>

<h4 style="text-align: justify;">
  The lessons to learn
</h4>

<p style="text-align: justify;">
  If you&#8217;re a programmer, remember: <strong>always double-check the data that the other side sent you</strong> before you use it to control the operation of your own code.
</p>

<p style="text-align: justify;">
  And remember: buffer overflows should always be treated as serious, even if they don&#8217;t lead to remote code execution.
</p>

<p style="text-align: justify;">
  Data leakage bugs can be just as disastrous, as this flaw demonstrates.
</p>

<h4 style="text-align: justify;">
  For further information&#8230;
</h4>

<p style="text-align: justify;">
  If you&#8217;d like to know more about the main sorts of vulnerablity, from RCE (remote code execution) through EoP (elevation of privilege) to Information Disclosure, please listen to our <a href="http://nakedsecurity.sophos.com/2013/09/18/sophos-techknow-understanding-vulnerabilties-podcast/">Techknow podcast</a>, <em>Understanding Vulnerabilities.</em>
</p>

<p style="text-align: justify;">
  This post totally copied from &#8220;<a href="http://www.theverge.com/">The Verge</a>&#8221; and &#8220;<a href="http://nakedsecurity.sophos.com/">SOPHOS</a>&#8220;. This is just an informative post.
</p>