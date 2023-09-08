---
title:       "Reusing Persistent SSH Connections for Performance Reasons"
type:        blog
date:        2012-04-30
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/375 ]
blog categories: [ "admin", "programming", "linux", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
Some weeks ago I had to run a simulation for my research which has been very elaborate and involved externally invoked scripts on remote machines (so-called Wuchtbrummen). These external calls were dispatched by a central main script, that was running on my local PC. To avoid a complete SSH session setup and teardown every time a new call should be invoked on a Wuchtbrumme, I wanted to have a persistent SSH connection, where all subsequent commands can be tunneled through.

<!--break-->
I was pretty surpised when I saw this available using standard OpenSSH options. I also posted this on [serverfault](http://serverfault.com/questions/216125/how-can-i-create-persistent-ssh-connection-to-stream-commands-over-a-period-of/354234#354234 "ServerFault"), even though I was a bit late to get the 'best answer badge'. I just post the necessary steps here to share it with you and to have it quickly searchable at hand.

The main option to set is the `ControlMaster` option. To enable it, I add the following line to `~/.ssh/ssh_config`

	ControlMaster auto

Then, I added the following line to the Host Section in `~/.ssh/ssh_config`

	Host *
	  ControlPath ~/.ssh/master-%r@%h:%p

Now start a master session in the background, which all subsequent SSH sessions will reuse using the following command (substitute remote.host with your remote machine or Wuchtbrumme):

	ssh -MNf remotehost

And that's it again!  
Cheers, iss
