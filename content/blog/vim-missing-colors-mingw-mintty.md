---
title:       "Vim is missing colors in MinGW when using mintty"
type:        blog
date:        2013-11-20
draft:       false
promote:     true
sticky:      false
aliases:     [ node/441 ]
blog categories: [ "operating systems", "windows" ]
flattr username: [ "nesono" ]

---

<!--more-->
For some weeks I had to cope with a monochrome vim in MSYS/MinGW, which turned out to be a really horrible experience to be honest and I avoided vim as often as I could.
Searching on the web did not help much, therefore I want to share the little thing with you
<!--break-->
The problem was that I was setting the `TERM` system environment variable in mintty (using the settings in the upper left corner) to xterm-256colors.

The solution was to reset the `TERM` system environment variable to **xterm**.

The colors instantly came back I was able to use my full dotfiles repository (except for UltiSnips due to the dependency on python) in MinGW - I seem to have a working system again after all this time...

That's it, cheers!  
iss
