---
title:       "List all svn externals in an SVN tree"
type:        blog
date:        2013-07-01
draft:       false
promote:     true
sticky:      false
aliases:     [ node/431 ]
blog categories: [ "programming", "bash", "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
While working with unfamiliar and large svn trees I was wondering how I can get all svn externals within the source tree on the command line.
As almost always, [stackoverflow][1] has the answer:

```bash
svn pg svn:externals -R
```

That's it again and cheers!  
iss

[1]: http://stackoverflow.com/questions/3725266/how-to-find-all-entries-in-svn-repo-with-an-external-to-a-given-url
