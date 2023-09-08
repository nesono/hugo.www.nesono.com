---
title:       "Brew install R fails - Updated right away"
type:        blog
date:        2012-09-25
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/407 ]
blog categories: [ "admin", "operating systems", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
I just cleaned up my home brew cellar and had problems reinstalling R.
I got the old well-known error message:

	brew install r
	==> Downloading http://cran.r-project.org/src/base/R-2/R-2.15.1.tar.gz
	Already downloaded: /Library/Caches/Homebrew/r-2.15.1.tar.gz
	Error: This formula requires a fortran compiler,...

Reinstalling gfortran (which was actually installed already) did not help and so I decided to trick home brew until the problem is fixed, with the following:

	export FC=`which gfortran`
	brew install r

Surprise surprise, it worked! :]

[**Update:**] The bug I filed was almost fixed immediately. So the post remains just as a reminder for the future ;)

Cheers,  
iss
