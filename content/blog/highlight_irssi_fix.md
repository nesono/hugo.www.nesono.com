---
title:       "Fixing the highlight window in IRSSI after restart"
type:        blog
date:        2013-11-19
changed:     2014-04-16
draft:       false
promote:     true
sticky:      false
aliases:     [ node/440 ]
blog categories: [ "linux", "os x", "ubuntu", "unix", "admin" ]
flattr username: [ "nesono" ]

---

<!--more-->
After reading an article on [quadpoint.org][1] I have been configured my [IRSSI][2] irc client with a highlight window as suggested by the author.
Since I am running IRSSI in a [screen][3]/[tmux][4] environment, I only need to restart it when my (virtual) machine has been restarted, which is rarely the case.
However, after restart, the highlight window is rarely in the right place.
<!--break-->
To work around that, I am using the following steps to regain original window layout. I am sharing them with you as it might either help you getting your layout back or you might help us finding a better solution.

First of all, I switch to the highlight window using the escape key.
Then, I am invoking the following commands:

```irc
/wc
/window new split
/window size 16
/hilight nesono
```

Do not forget to change `nesono` to your username instead.  
Happy IRSSI'ng,  

iss

[1]: http://quadpoint.org/articles/irssi/ "A Guide to Efficiently Using Irssi and Screen"
[2]: http://www.irssi.org "IRSSI home page"
[3]: https://www.gnu.org/software/screen/ "GNU screen"
[4]: http://tmux.sourceforge.net "tmux home page"
