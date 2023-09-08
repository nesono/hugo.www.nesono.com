---
title:       "Get rid of row names in R"
type:        blog
date:        2015-03-11
draft:       false
promote:     true
sticky:      false
aliases:     [ node/456 ]
blog categories: [ "r" ]
flattr username: [ "nesono" ]

---

Yesterday I had to remind myself on how to remove the row names in a `data.frame`.
Row names are usually added by filtering steps such as `subset`, etc.

Assume we want to remove the row names of the `data.frame` called `data`, we can type:

```r
rownames(data) <- c()
```

That's it  
iss
