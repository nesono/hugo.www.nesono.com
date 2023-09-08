---
title:       "Mounting a ZFS ZPool (RaidZ) from a FreeBSD Rescue System"
type:        blog
date:        2015-03-08
draft:       false
promote:     true
sticky:      false
aliases:     [ node/455 ]
blog categories: [ "freebsd" ]
flattr username: [ "nesono" ]

---

<!--more-->
If you happen to lock yourself out of your own remote system with no hardware access to the server you mind end up in the same panic as me tonight.
Since it took me surprisingly long, I thought it might be helpful to write the steps down to get a zpool mounted on a rescue (FreeBSD) system.
<!--break-->
I found the solution - surprise, surprise - in the FreeBSD [handbook][1].
I was reluctant to believe the handbook, since it did not require me to actually provide any drive name/id.

First, I had to start the ZFS service.
```bash
service zfs onestart
```
Then, I could import the pool, even though I had to force the import since the pool was previously used by another machine (my server) without exporting it.
```bash
zpool import -f
```

Note that your root will be exchanged to contain the zpool contents unless you change the mount point of the pool. I didn't change it and it worked fine, but your mileage may vary.
Just remember to change the mount point back before you reboot.

That's it  
Cheers,  
iss

[1]: https://www.freebsd.org/doc/handbook/zfs-quickstart.html  "FreeBSD Handbook ZFS"
