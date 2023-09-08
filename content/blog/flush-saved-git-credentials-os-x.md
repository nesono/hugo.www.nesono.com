---
title:       "Flush Saved Git Credentials on OS X"
type:        blog
date:        2015-05-11
draft:       false
promote:     true
sticky:      false
aliases:     [ node/463 ]
flattr username: [ "nesono" ]
blog categories: [ "scm" ]

---

<!--more-->
I did not find anything on the web I thought I'd paste this here for anyone else running into this issue. I had to change the stored credentials for a git server and starting the OS X keychain failed with a strange error message that the stored password was bound to a specific user (which I naively assumed was me).
<!--break-->
If you run into the same issue, you might want to erase all saved git credentials using the following command:

```bash
git-credential-osxkeychain erase
```

After that, you can enter your new/old credentials again after being prompted by git.  
That's it again,  
iss
