---
title:       "Let Postfix 'listen' on 465 and 587"
type:        blog
date:        2013-03-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/430 ]
blog categories: [ "admin", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
Check out the recent update on my mail server documentation [here][1].
After years of using my mail server actively, I finally changed to an ISP that blocks port 25, so I had to add the two ports from the head line to the postfix ports.
However, the solution did not turn out to be straight forward but involved iptables rules.

Just follow above link and read on.

Cheers,  
iss

[1]: https://www.nesono.com/node/429 "Add iptables Rules for Postfix to Support Ports 465 and 587"
