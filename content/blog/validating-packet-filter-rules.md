---
title:       "Validating Packet Filter rules"
type:        blog
date:        2015-04-20
draft:       false
promote:     true
sticky:      false
aliases:     [ node/462 ]
blog categories: [ "freebsd" ]
flattr username: [ "nesono" ]

---

<!--more-->
After editing Packet Filter rules you might want to verify what you just edited before enabling the rules.
Here is what I usually do on my server to not screw up the whole installation and being able to quickly get back to my previous configuration.
<!--break-->
First of all, I change `pf_enable` in `/etc/pf.conf` to `NO`.
This makes it easier to disable the packet filter in case you lock yourself out of the server due to a bad rule.
To disable it, I just have to reboot, which is possible through my providers web interface.

Next, I let `pfctl` parse and print the rules as it understands them.
I use the following command to do that:

```bash
pfctl -nvvvf /etc/pf.conf
```

Note that your packet filter configuration file might have a different name.
Cheers,  
iss
