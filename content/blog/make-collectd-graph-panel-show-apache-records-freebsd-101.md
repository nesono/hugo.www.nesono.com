---
title:       "Make Collectd Graph Panel show Apache records on FreeBSD 10.1"
type:        blog
date:        2015-06-01
draft:       false
promote:     true
sticky:      false
aliases:     [ node/464 ]
blog categories: [ "freebsd" ]
flattr username: [ "nesono" ]

---

<!--more-->
I just patched the installation of [Collectd Graph Panel][1] to make it work together with [Collectd][2] version 4.10 on [FreeBSD][3] 10.1. The value string in the Collectd Graph Panel did no longer match the (old) Collectd `rrd` data.

<!--break-->

I used the attached patch to fix it. You can simply download the patch file and run the following command in your checked out version of the Collectd Graph Panel:

```bash
git apply collect.patch
```

That's it again and cheers,  
iss

[1]: https://github.com/pommi/CGP "Collectd Graph Panel Website"
[2]: https://collectd.org "Collectd Website"
[3]: https://www.freebsd.org "FreeBSD Website"
