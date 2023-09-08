---
title:       "Disable GNOME Keyring When Moving From GNOME to KDE"
type:        blog
date:        2012-07-11
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/388 ]
blog categories: [ "linux", "ubuntu", "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
or how to get rid of:  
`p11-kit: couldn't load module: /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so`

After I moved my ubuntu desktop to kubuntu, the gnome-keyring always was started at every login, asking for my password. Besides the fact, that gnome-keyring does not feel native when working on KDE, every time I invoked `svn` in the terminal, I saw the error message from the subtitle.
The solution was pretty tedious to find, so I hope to save you and myself some time if this will happen again.
<!--break-->

First of all, I tried to get some more information about this p11-kit stuff and thus installed p11-kit (which might already be installed on your site).

	sudo aptitude install p11-kit

I called `p11-kit -v -l` to get some information about what's actually happening in the background and got the message that the bad configuration file has the name `/etc/pkcs11/modules/gnome-keyring-module`.
It is part of the package gnome-keyring (surprise, surprise):

	apt-file search /etc/pkcs11/modules/gnome-keyring-module
	gnome-keyring: /etc/pkcs11/modules/gnome-keyring-module

Obviously, I had to purge the configuration files from gnome-keyring to get rid of the configuration file and shared object.

	sudo aptitude purge gnome-keyring

Unfortunately, subversion now crashes randomly but frequently with a core dump. I removed the gnome keyring configuration, kde wallet and subversion configuration files.

	rm -r ~/.gnome2/keyrings
	rm -r ~/.subversion
	find ~/.kde -iname \*wallet\* -exec rm -r {} \;

Which is basically a good idea, but did not solve the *SEGFAULT*.
Finally, I installed gnome-keyring (again), and purged it (again), which seems to have taken away all my pain and now everything is fine - until the end...

	sudo aptitude install gnome-keyring
	sudo aptitude purge gnome-keyring

Cheers,  
iss
