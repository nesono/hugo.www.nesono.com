---
title:       "R tikzDevice Package Moved to Archive on CRAN"
type:        blog
date:        2012-09-12
changed:     2012-09-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/403 ]
blog categories: [ "programming", "r" ]
flattr username: [ "nesono" ]

---

<!--more-->
Last week I wanted to change some figures in a presentation I once made with R's tikzDevice and was faced with the [fact][1] that the package has been moved to CRAN's archive.
<!--break-->
My mail to the authors was quickly replied and offered a workaround:

> ...
> The development build of tikzDevice 0.7 haven't gone through all the testing
> required for a CRAN release, but it should be free of any major bugs.
> You can install from R-Forge thusly:
> install.packages('tikzDevice', repos='http://r-forge.r-project.org')

However, I got the following error (stripped version):

	ERROR: dependency ‘filehash’ is not available for package ‘tikzDevice’
	installation of package ‘tikzDevice’ had non-zero exit status

Thus, I installed the `filehash` package:

```r
install.packages( 'filehash' )
```

And ran the install command for the `tikzDevice` again:

```r
install.packages('tikzDevice', repos='http://r-forge.r-project.org')
```

That's it,  
iss

**Update:**
Thanks to Ben, you can also use this one liner:
```r
install.packages( 'tikzDevice', repos=c('http://r-forge.r-project.org',getOption("repos")) )
```

[1]: http://cran.r-project.org/web/packages/tikzDevice/index.html "CRAN tikzDevice"
