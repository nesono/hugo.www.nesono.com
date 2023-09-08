---
title:       "Create set plots or an alternative histogram or barplot with R"
type:        blog
date:        2015-03-11
changed:     2015-03-12
draft:       false
promote:     true
sticky:      false
aliases:     [ node/458 ]
blog categories: [ "r" ]
flattr username: [ "nesono" ]

---

<!--more-->
To create a stem plot, barplot (with filled bars), or a histogram, there is a simple method in R which provides a flexible alternative to the full blown barplot and histogram plots.
It's even easier when it comes to composing multiple graphs in one plot.
<!--break-->

Simply use the type `h` to create a stem plot:
```R
plot( type='h', ... )
```
In case you want to have a barplot or histogram it's wise to use square line endings and change the line width (requires tweaking):
```R
plot( type='h', lend=2, lwd=30 )
```

That's it  
iss
