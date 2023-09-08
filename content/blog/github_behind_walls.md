---
title:       "Github Behind Walls"
type:        blog
date:        2012-08-20
changed:     2012-09-24
draft:       false
promote:     true
sticky:      false
aliases:     [ node/401 ]
flattr username: [ "nesono" ]
blog categories: [ "admin", "scm" ]

---

<!--more-->
What a nice [post][1] on [Stackoverflow][2]!
Just paste the following lines into your `.ssh/config` file and let SSH redirect to `ssh.github.com`<!--break-->

	Host github.com
	  User YourUserName
	  Port 443
	  Hostname ssh.github.com

And I was actually struggling with https all the time...  
pfffffffff,  
iss

[1]: http://stackoverflow.com/questions/7953806/github-ssh-via-public-wifi-port-22-blocked "github SSH Via Public Wifi Port 22 Blocked"
[2]: http://stackoverflow.com "Stackoverflow"
