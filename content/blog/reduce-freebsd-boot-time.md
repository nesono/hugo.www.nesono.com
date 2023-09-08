---
title:       "Reduce FreeBSD boot time"
type:        blog
date:        2015-04-19
draft:       false
promote:     true
sticky:      false
aliases:     [ node/461 ]
flattr username: [ "nesono" ]
blog categories: [ "freebsd" ]

---

<!--more-->
The default boot delay under FreeBSD is 10 seconds. This can drive you crazy if your server is down.
<!--break-->
To disable any autobot delay, you can use either an `autobot_delay` value of `"0"` to disable delay, or `"-1"` to even make it impossible for the user to interrupt autoboot. I am using the following setting in `/boot/loader.conf`:

```conf
autoboot_delay="0"
```

That's it. Cheers,  
iss
