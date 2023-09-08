---
title:       "Grub Configuration Booting FreeBSD on Existing Ubuntu"
type:        blog
date:        2012-05-11
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/377 ]
blog categories: [ "operating systems", "linux", "ubuntu" ]
flattr username: [ "nesono" ]

---

<!--more-->
For doing native FreeBSD stuff, I decided to install FreeBSD besides an existing Ubuntu installation. However, the Grub settings did not turned out to be as easy as the installation process.
<!--break-->

I installed the system on partition `3` of a SDD, which is `/dev/sda1` on my the Ubuntu machine and connected to the first SATA slot. Here are the lines I added to `/etc/grub.d/40_custom`:

	menuentry "FreeBSD" --class freebsd --class bsd --class os {
	          insmod ufs2
	          set root='(hd0,2)'
	          chainloader +1
	}

And that's it, again :)
