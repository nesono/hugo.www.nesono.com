---
title:       "rm2trash for OS X update"
type:        blog
date:        2011-11-26
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/369 ]
blog categories: [ "programming", "zsh", "apple script", "operating systems", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
I recently updated the shell add-on for OS X, that overloads rm to not remove the items, but move them into trash instead. Before the update, a for loop moved every single item given in the command line into trash using one osascript (Apple Script) call per item. This caused a blocking shell with one 'flupp' sound effect for each moved item, which can be quite tedious, when removing many items, even if they are small. Now, after the update, a item list is created and filled with all given items to remove and in the end passed to one osascript call.

The change is committed to [my github repo](https://github.com/nesono/nesono-bin/blob/master/bashtils/rm2trash.darwin "my github repo"), as usual.

Best,  
iss

