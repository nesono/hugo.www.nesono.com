---
title:       "WinDbg breakpoint stuff"
type:        blog
date:        2015-08-04
changed:     2015-08-05
draft:       false
promote:     true
sticky:      false
aliases:     [ node/465 ]
blog categories: [ "windows" ]
flattr username: [ "nesono" ]

---

<!--more-->
For my future self, I jot down some useful WinDbg commands here. It contains standard breakpoint handling and running - just the very simple basics I should never forget.
First of all, make sure you are using workspaces if you want to save the session (breakpoints, executable, etc.). Note that this document will grow over time, hopefully.

Depending on the task you might find those commands useful:

| command | description              | example |
| ------- | ------------------------ | ------- |
| bm      | set breakpoint at symbol | bm YourApplication.exe!*Symbolname* (supports wildcards) |
| bl      | list breakpoints         | bl      |
| bc      | clear breakpoints        | bc * / bc 5-28 / bc 1 4 6 |
| g       | go / run application     | g       |
| .reload | reload application       | .reload /f |

That's it,  
iss
