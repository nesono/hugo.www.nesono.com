---
title:       "Exchange a broken hard drive in a running ZFS pool"
type:        iss_doc_book
date:        2014-09-23
draft:       false
promote:     true
sticky:      false
aliases:     [ node/453 ]
flattr username: [ "nesono" ]

---

<!--more-->
If one of your hard drives dies on your FreeBSD server, you need to format the new hard disk in the exactly same layout as the existing/previous disk was formatted.
Last time when one of my hard drives started failing, I used the following steps to match up the partition layout between the new and the old (still working) hard drive.
<!--break-->
First I figured out the layout of the existing hard disk (in this case `ada1`)
```bash
gpart show ada1
=>        34  3907029101  ada1  GPT  (1.8T)
          34           6        - free -  (3.0K)
          40         128     1  freebsd-boot  (64K)
         168     8388608     2  freebsd-swap  (4.0G)
     8388776  3898640352     3  freebsd-zfs  (1.8T)
  3907029128           7        - free -  (3.5K)
```

Then I created the GPT on the new disk (`ada0`):
```bash
gpart create -s gpt ada0
```

Add the boot section:
```bash
gpart add -b 40 -s 128 -t freebsd-boot ada0
```

Set the boot code:
```bash
gpart bootcode -b /boot/pmbr -p /boot/gptzfsboot -i 1 ada0
```

Create the swap partition:
```bash
gpart add -s 8388608 -t freebsd-swap -l swap10 ada0
```

Add the ZFS partition:
```bash
gpart add -t freebsd-zfs -l disk10 ada0
```

Then take the disk online:
```bash
zpool online tank /dev/ada0p3
```

And finally start resilvering:
```bash
zpool replace tank /dev/ada0p3
```

That's it.  
iss

