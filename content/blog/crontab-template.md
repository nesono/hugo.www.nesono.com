---
title:       "Crontab Template"
type:        blog
date:        2009-11-02
changed:     2017-12-06
draft:       false
promote:     true
sticky:      false
aliases:     [ node/262 ]
blog categories: [ "operating systems", "linux", "os x", "ubuntu", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
I just found my good old crontab template, which provides some nice formatting and documentation features. Just for our convenience, I paste it in here.
<!--break-->

	# .---------------- minute (0 - 59)
	# |  .------------- hour (0 - 23)
	# |  |  .---------- day of month (1 - 31)
	# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
	# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)  OR sun,mon,tue,wed,thu,fri,sat
	# |  |  |  |  |
	# *  *  *  *  *  command to be executed
	# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1

You don't need to care about the artificial line break too much - it's only in the html display, simply select above text and copy it to the start of your crontab file.

Enjoy and relax, iss!
