---
title:       "MacPorts Selfupdate Problems"
type:        blog
date:        2010-11-19
changed:     2012-09-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/337 ]
blog categories: [ "admin", "operating systems", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
If you experience the same errors like me:

	Error: /opt/local/bin/port: port selfupdate failed: Error installing new MacPorts base: shell command failed

Then, you might have the wrong gcc active. You can use my [script][1] to switch your gcc back to the system's standard, which is gcc-4.2 in my case.

Cheers,  
iss

[1]: https://github.com/nesono/nesono-bin/blob/master/switchgcc.sh "switchgcc.sh on github"
