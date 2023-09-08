---
title:       "Lldb Breakpoint Stuff"
type:        blog
date:        2015-08-05
draft:       false
promote:     true
sticky:      false
aliases:     [ node/466 ]
blog categories: [ "os x", "programming", "c/c++", "xcode" ]
flattr username: [ "nesono" ]

---

<!--more-->
Just like in my previous [post][1] I need to jot down some useful commands for Lldb because I need to look them up so often. It contains standard breakpoint handling and running - just the very simple basics I should never forget. Note that this document will grow over time, hopefully.

First of all, do not forget to prepend xcrun to lldb, that makes it much more useable:

<pre><code class="bash">xcrun lldb <executable></code></pre>

Depending on the task you might find those commands useful:

| command | description              | example |
| ------- | ------------------------ | ------- |
| br s -M | set breakpoint at method | br s -M *Symbolname* |
| br l    | list breakpoints         | br l    |
| br del  | delete breakpoints       | br del / br del 5 / br del 1.4 |
| r       | go / run application     | r       |
| thread until N | run application until a certain line | thread until 100 |

That's it,  
iss

[1]: https://www.nesono.com/content/windbg-breakpoint-stuff "WinDbg Breakpoint Stuff"
