---
title:       "LaTeX tikz main_memory problems on OS X"
type:        blog
date:        2014-02-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/443 ]
blog categories: [ "os x", "latex", "r" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I had to increase the main memory of my LaTeX installation yet another time and it required quite a while to collect the information again.
Therefore, I am pasting my steps here as a future reference.
<!--break-->

First of all, this is the error message I try to get rid of:

```bash
! TeX capacity exceeded, sorry [main memory size=5000000].
```

It is caused by my `tikz` figures that have been created using the `tikzDevice` package for `R`.

I fixed my problem using the following steps:

* Open the specific `texmf.cnf` and go to line 697:  
```bash
sudo vim /usr/local/texlive/2013/texmf-dist/web2c/texmf.cnf +697
```
* Change the value `main_memory` to 9000000 (was enough for me).
* Run fmutil helper script:  
```bash
sudo fmtutil-sys --all
```

After that LaTeX ran fine again.  
That's it,  
iss
