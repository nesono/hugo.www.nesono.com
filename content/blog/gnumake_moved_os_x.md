---
title:       "GNU/Make moved in OS X 10.8 Mountain Lion -- Updated"
type:        blog
date:        2012-08-08
changed:     2012-08-14
draft:       false
promote:     true
sticky:      false
aliases:     [ node/399 ]
blog categories: [ "programming", "xcode", "c/c++", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
What a bad surprise, trying to build the Makefile-based project and got the response: `make not found`!  
Lucky for us, it has just moved into the XCode package - the logical place according to Apple's rules, though not automatically in the `PATH` environment variable :/
<!--break-->

Just add the following path to your PATH variable:  
`/Applications/Xcode.app/Contents/Developer/usr/bin`

**[Update:]** It's actually much easier, though a little hidden: Just install the `Command Line Tools` from Preferences -> Downloads :]

Cheerio,  
iss
