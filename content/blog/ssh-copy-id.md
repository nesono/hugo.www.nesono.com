---
title:       "Add SSH Public Key With One Command"
type:        blog
date:        2011-11-16
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/367 ]
blog categories: [ "admin", "operating systems", "linux", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
As I always forget the exact syntax and am too chicken-hearted to fool around, I note down the command to add one's public key to the authorized keys on the remote machine (to login using pub/private key pair only) here.
Use the following command (id_rsa.pub might be id_dsa.pub on your site).

<pre><code class="bash">cat ~/.ssh/id_rsa.pub | ssh user@site.com "cat - >> ~/.ssh/authorized_keys"</code></pre>

That's it,  
iss
