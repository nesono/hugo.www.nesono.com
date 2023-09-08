---
title:       "Dump gcc Preprocessor Macro Definitions"
type:        blog
date:        2010-06-09
changed:     2012-09-30
draft:       false
promote:     true
sticky:      false
aliases:     [ node/289 ]
flattr username: [ "nesono" ]
blog categories: [ "programming", "c/c++" ]

---

<!--more-->
Today I wanted to get all macro definitions from gcc - including those defined internally. I knew it some tim ago, but forgot the command again, so I paste it in here for all of you.

```bash
gcc -dM -E - < /dev/null | sort
```

That's it and cheers,  
iss
