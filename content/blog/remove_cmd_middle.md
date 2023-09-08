---
title:       "Remove Old Snow Leopard Shortcut For Spaces - Cmd-Middle Button"
type:        blog
date:        2011-07-23
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/362 ]
blog categories: [ "operating systems", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
It's a bit tricky, but today I fixed a small problem of an obsolete shortcut in OS X Lion.
I used to have Cmd-Right on Expos&eacute; and Cmd-Middle on Spaces, to have both functions short at hand.
After I upgraded to Lion from Snow Leopard, Spaces and Expos&eacute; are merged into Mission Control, which was a wise decision, but my mouse shortcuts were migrated BOTH to Mission Control.
Great not to loose the shortcuts, but bad not to be able to change them again - Cmd-Middle has been vanished from System Preferences and only Cmd-Right showed up as a shortcut for Mission Control.

An now for the solution:&nbsp;Lucky me, my other Mac was still on Snow Leopard and I could check which file contains the Cmd-Middle shortcut.
I did this by using <a href="http://fernlightning.com/doku.php?id=software:fseventer:start" target="_blank">fseventer</a>, a tool to display file system events recorded by OS X.
It showed me, that `~/Library/Preferences/com.apple.hotkeyshortcut.plist` was the file in charge. I then made a copy of the old file and disabled the shortcut temporarily.
Then I checked, what changed in the file by using FileMerge (comes with XCode IIRC) and using <a href="http://jasonfharris.com/blog/2010/04/make-filemerge-diff-plist-files/" target="_blank">this</a> additional trick.
The result is given in the picture.

<a href="/sites/default/files/imagecache/fullsize/images/CmdMiddleShortcutRemoval.png"><img alt="" src="/sites/default/files/imagecache/thumbnail/images/CmdMiddleShortcutRemoval.png" /></a>

The file was renamed for Lion however and is called `com.apple.symbolichotkeys.plist` now.
Then, I edited the file using my favourite editor (vim), but before I had to convert it to xml format using the following line

	plutil -convert xml1 com.apple.symbolichotkeys.plist

After fixing the lines for key 87 and key 88, I converted the file back using:

	plutil -convert binary1 com.apple.symbolichotkeys.plist

And that's it again,  
cheers!  
iss
