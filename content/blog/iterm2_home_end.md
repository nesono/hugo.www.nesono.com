---
title:       "iTerm2 Home and End Buttons"
type:        blog
date:        2011-04-15
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/351 ]
blog categories: [ "admin", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
After being somewhat unhappy with the Apple Terminal application since the very beginning, I found a very nice alternative in [iTerm2][1]! 
Everything seems to work fine from tabbing, splitting horizontally and vertically, cursor observation to fancy growl support.
<!--break-->

The only pain were misconfigured Home and End keys. The approriate information on the iTerm2 homepage did not really give me the solution right out of the box, so I paste it here.

Make sure that your TERM variable is the same as set in your iTerm2 profile (in preferences) and add the following two esape sequences to your key configuration:

Button | Escape Sequence
------ | ---------------
Home   | Esc + [1~
End    | Esc + [4~

It should work right after adding the sequences!  
That's it,  
Cheers!  
iss

[1]: http://www.iterm2.com/#/section/home "iTerm2 Home Page"
