---
title:       "Insert Output from Command Line in Vim"
type:        blog
date:        2011-08-02
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/364 ]
blog categories: [ "programming" ]
flattr username: [ "nesono" ]

---

<!--more-->
I just figured out once more, that vim works as expected. If you need to insert the output (e.g., stdout) from a command into the open buffer, e.g. to insert a certain type of files into something like .gitignore, svn::ignore, .cvsignore, you can simply type
<!--break-->

	:r !ls *.aux

In command mode and the text will be inserted at the cursor position.

Cheers,  
iss
