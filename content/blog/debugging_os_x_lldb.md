---
title:       "Debugging in the Terminal on OS X with LLDB"
type:        blog
date:        2015-02-02
draft:       false
promote:     true
sticky:      false
aliases:     [ node/454 ]
blog categories: [ "os x", "programming", "c/c++", "xcode" ]
flattr username: [ "nesono" ]

---

<!--more-->
Since I happen to forget this every once in a while and end up in trying to debug in the command line but no symbols and no source is found, I drop a message for my future me:
<!--break-->
"Run lldb inside the xcrun enviroment:"

```bash
xcrun lldb [binary]
```

This seems to work fine for Xcode, Unix Makefiles (gmake), as well as ninja projects (created with CMake). Cheers,  
iss
