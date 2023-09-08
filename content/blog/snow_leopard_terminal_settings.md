---
title:       "Refine (Snow) Leopard Terminal Settings"
type:        blog
date:        2009-09-11
changed:     2012-10-02
draft:       false
promote:     true
sticky:      false
aliases:     [ node/248 ]
blog categories: [ "operating systems", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
The Mac OS&nbsp;X Terminal is not a terminal, as other *nix users might be used to.
Things like history-search-backward/forward, word-wise jumping, terminal window scrolling by page-up/down - all these are disabled by the standard terminal settings.
<!--break-->

Today I had to fight against character codes of an Irssi™ client, in a remote Screen™ session on a Linux™ server.
It turned out to be a good idea to dig into the terminal settings and try to configure the terminal, as I was used to on my other *nix machines.
For Irssi, had to do some additional `~/.inputrc` tweaks and adjust some locale settings I attached at the end of the entry.


First of all, I changed the preferences of the Terminal application, which can be reached by the menu bar or simply pressing the preferences shortcut (⌘+,).
The following pictures show all settings I modified or added.

<table><tbody><tr><td class="rtecenter"><p><a href="/sites/default/files/images/Term_Pref_Window.png" rel="shadowbox[SLterminal]"><img alt="" class="image" src="/sites/default/files/imagecache/thumbnail/images/Term_Pref_Window.png" style="width: 100px; height: 80px; "></a></p></td><td><p align="center"><a href="/sites/default/files/images/Term_Pref_Key_1.png" rel="shadowbox[SLterminal]"><img alt="" class="image" src="/sites/default/files/imagecache/thumbnail/images/Term_Pref_Key_1.png" style="width: 100px; height: 80px; "></a></p></td><td><p align="center"><a href="/sites/default/files/images/Term_Pref_Key_2.png" rel="shadowbox[SLterminal]"><img alt="" class="image" src="/sites/default/files/imagecache/thumbnail/images/Term_Pref_Key_2.png" style="width: 100px; height: 80px; "></a></p></td><td><p align="center"><a href="/sites/default/files/images/Term_Pref_Key_3.png" rel="shadowbox[SLterminal]"><img alt="" class="image" src="/sites/default/files/imagecache/thumbnail/images/Term_Pref_Key_3.png" style="width: 100px; height: 80px; "></a></p></td><td><p align="center"><a href="/sites/default/files/images/Term_Pref_Advanced.png" rel="shadowbox[SLterminal]"><img alt="" class="image" src="/sites/default/files/imagecache/thumbnail/images/Term_Pref_Advanced.png" style="width: 100px; height: 80px; "></a></p></td></tr></tbody></table>

Or in words:

* Set the history length of the terminal to something decent (or to unlimited)
* Adjust the Terminal window size by setting the columns and lines 
* Add some Key-Action tupels to the Keyboard section (pics 2,3,4) 
* Make sure, that delete sends Ctrl-H (beware, that this behaves bad under `GNU/screen` - the only solution I know is `zsh` for this) 
* Set character coding to UTF-8

In my `~/.inputrc` file, I have the following lines:

	# allow the use of the Home/End keys
	"\e[1~": beginning-of-line
	"\e[4~": end-of-line
	
	# allow the use of the Delete/Insert keys
	"\e[3~": delete-char
	"\e[2~": quoted-insert
	
	# alternate mappings for "page up" and "page down" to search the history
	"\e[5~": history-search-backward
	"\e[6~": history-search-forward
	
	# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
	"\e[1;5C": forward-word
	"\e[1;5D": backward-word
	"\e[5C": forward-word
	"\e[5D": backward-word
	"\e\e[C": forward-word
	"\e\e[D": backward-word

In my local `~/.profile`:

	# for umlauts, etc...
	export LC_ALL="en_US.UTF-8"
	export LANG="en_US.UTF-8"

And on the remote side's (Ubuntu) `~/.bashrc`:

	export LANG=en_US.UTF-8
	export LANGUAGE=en_US.UTF-8
	export LC_ALL=en_US.UTF-8

Additionally, I added a ~/.screenrc on my remote host with the following line:
```bash
utf8 on on
```

Now, everything should run fine, even with unicode :)  
But was that really easy?

Cheers, iss
