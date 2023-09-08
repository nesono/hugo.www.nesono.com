---
title:       "Download the Right FreeBSD Kernel Source Code"
type:        blog
date:        2014-04-14
draft:       false
promote:     true
sticky:      false
aliases:     [ node/445 ]
blog categories: [ "operating systems", "freebsd" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I wanted to download the right kernel source code and found [this helping blog post][1].
However, I got the feeling that the url can be built automatically to avoid fetching the wrong URL.
Use the following command instead and it should always fetch the appropriate sources according to your currently running machine:

<pre><code class="bash">fetch ftp://ftp.freebsd.org/pub/`uname -s`/releases/`uname -m`/`uname -r`/src.txz</code></pre>

I hope this was at least a little helpful ;)  
Cheers,  
iss

[1]: http://www.netroby.com/view.php?id=3595#.U0xJbuaSxQ4
