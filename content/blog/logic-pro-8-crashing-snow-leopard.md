---
title:       "Logic Pro 8 crashing frequently under Snow Leopard"
type:        blog
date:        2009-10-08
changed:     2012-09-30
draft:       false
promote:     true
sticky:      false
aliases:     [ node/259 ]
blog categories: [ "creative", "music" ]
flattr username: [ "nesono" ]

---

<!--more-->
While using it for quite a while now and without serious problems, Snow Leopard seems to work together with Logic Pro 8 no longer! It's really suspicious, that it suddenly began to crash almost every time, I wanted to use it and several reports from other users seem to prove the same:

* [macosxhints][1]
* [logic pro help][2]
* [cnet forums][3]

The only thing supposing to work is upgrading to Logic Pro 9 - very funny Steve!
So, if you need to work with Logic Pro 8, don't upgrade your Leopard!

**[Update]**
In the following I describe the setup I am using after the shock fade-out.
Since I was reluctant towards downgrading and spent time trying different hardware connection orders, I came up with an interesting solution.
First of all, I upgraded to Logic Pro 9 (gnn), bad enough, Logic 9 did freeze as well whenever I plugged my Fireface 400 to my mac (took me while to discover).
I searched through the archives of RME and they claimed a possible bug in the Firewire driver interface connection handling routine framework (funny by purpose) and the only way I could get my Fireface interface running was connecting it as soon, as the mac was on Power.
I am using a switchable power outlet for quite a while, so I simply attached the Fireface using its DC adapter to the same power outlet as the mac and switched the Fireface from bus powered to power supply.
Now, everytime I switch on the power outlet, the Fireface switches on automatically and then I boot my mac.
Maybe this can work for Logic 8 as well - I did not give it a try.
I am happy to have a stable setup now and am cured from hardware trials for quite a while...

Cheers, iss

[1]: http://forums.macosxhints.com/showthread.php?p=555528
[2]: http://www.logicprohelp.com/viewtopic.php?t=46921&sid=f8a5ce36bc2d33cd313c60af73cfe6e2
[3]: http://forums.cnet.com/5208-7592_102-0.html?threadID=357400
