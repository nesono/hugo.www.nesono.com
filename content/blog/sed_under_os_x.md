---
title:       "SED under Mac OS X 10.5"
type:        blog
date:        2009-09-22
changed:     2012-10-02
draft:       false
promote:     true
sticky:      false
aliases:     [ node/252 ]
blog categories: [ "bash", "os x", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I fixed a problem with a bash-script I was using for quite a while now, which refused to work correctly under Mac OS&nbsp;X 10.5 (maybe other versions as well). The Problem was, that an sed script did not substitute, what it ought to.
<!--break-->

The core problem simply had to do with extended regular expression under Mac OS&nbsp;X's sed! With Mac OS&nbsp;X, `+`, `|` and `?` do not mean the same as they do under e.g. Linux! I was using `+` and my sed script neglected the work :/

The fix was simply to **substitute all occurences of `+` by `\{1,\}`**, that's all :D  

Cheers, iss
