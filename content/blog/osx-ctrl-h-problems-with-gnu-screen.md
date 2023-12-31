---
title:       "Mac OS X Ctrl-H and/or Delete/Backspace Problems with GNU Screen [UPDATE]"
type:        blog
date:        2010-03-01
changed:     2012-09-30
draft:       false
promote:     true
sticky:      false
aliases:     [ node/284 ]
flattr username: [ "nesono" ]
blog categories: [ "admin", "os x" ]

---

<!--more-->
Today I found the issue of a problem, I struggled for quite a while!
With my Mac logging into my server and running some GNU Screen session on it, I had problems with backspace.
It was either interpreted as delete, or not interpreted at all.
Setting the *Preferences of Mac's Terminal to Ctrl-H* sending was not the solution either, as this disabled all special characters (using option-u for example).
Furthermore, I noticed several crashes of my ssh sessions.

Finally, I recognized, that the ssh client I was using was taken from `/opt/local/bin` instead of `/usr/bin`.
MacPorts has installed a new ssh client over mine "original" one.
So my solution was simply to change the ssh client by modifying the PATH variable.
Maybe this is not a solution for all time, but for today I'm fine ;)

**[UPDATE]** Finally, I found the actual issue here! 
When running `irssi` from screen directly, the TERM environment variable is not set.
Thus, I added the following function to my zshrc (bashrc should work the same way) and the problem was gone.
No more backspace problems under both irssi and vim!

	SCREENBIN=$(which screen)
	echo "using screen bin: ${SCREENBIN}"
	
	# function to fix screen Delete/Ctrl-H  problem
	function screen()
	{
	  OLDTERM=${TERM} && TERM=screen && ${SCREENBIN} $@ && TERM=${OLDTERM}
	}

Cheers,  
iss

[1]: http://www.nesono.com/node/308
