---
title:       "Change Folder When Proceeding to Next Unread Message in Postbox"
type:        blog
date:        2011-07-20
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/361 ]
blog categories: [ "os x" ]
flattr username: [ "nesono" ]

---

While trying [Postbox](http://www.postbox-inc.com/) under Mac, I soon realized it's a thunderbird derivative. However, using Thunderbird I was able to use the 'N' short cut to switch to next unread message no matter in which folder it resides. After senseless searches in the virtual Postbox documentation, I searched for it at Mozilla and found the result instantly. However, you need to edit the configuration by hand, which seems a bit nerdy for a comfortable Mac Application.

Therefore, open Postbox' preferences and switch to **Advanced-&gt;General**, press **Config Editor...** at the bottom and insert nav in the search field after pledging to be carefull. Then only one line should be left in the list below, labeled **mailnews.nav_crosses_folders**. Change it's value to **1** and that's it.

Cheers,  
iss

