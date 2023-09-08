---
title:       "Changing the From address field in /usr/bin/mail"
type:        blog
date:        2009-08-13
changed:     2012-10-04
draft:       false
promote:     true
sticky:      false
aliases:     [ node/247 ]
blog categories: [ "linux", "ubuntu", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I needed to send a mail to a mailing list, which I joined using an old mail address, which turned into an alias only address a while ago. I hence needed to send a single mail to the list with this old address and did not want to add it as an identity to my mail application - it simply wasn't worth the effort.
<!--break-->

Luckily, it is possible to overwrite the mail headers using the command line mail application under *nix and I simply logged into my server and sent the mail using the following command:

<pre><code class="bash">echo "your message text" | mail -a "From: other@domain.com" -s "your subject" dest@xxx.com</code></pre>

Nice, isn't it? Cheers, iss
