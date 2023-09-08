---
title:       "Using gitx from the Terminal"
type:        blog
date:        2010-05-27
changed:     2012-09-30
draft:       false
promote:     true
sticky:      false
aliases:     [ node/287 ]
blog categories: [ "programming", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
This information is neither new, nor secret, but useful by all means. 
Gitx, the git GUI for Mac OS X has additional functionality to be invoked from the Terminal right beside your favourite editor!

Select `Enable Terminal Usage...` from the GitX frontmost menu and enter your administrator password.
Make sure, that `/usr/local/bin` is in your `PATH` variable and try `gitx --help` from your Terminal.

If you want to start gitx from within Terminal inside your git repository in check-in mode, invoke

<pre><code class="bash">gitx -c</code></pre>

More details and further information can be found in the [user manual](http://gitx.frim.nl/user_manual.html "gitx homepage") on the gitx homepage.

Cheers,  
iss
