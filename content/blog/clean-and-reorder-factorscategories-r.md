---
title:       "Clean up and Reorder Factors/Categories in R"
type:        blog
date:        2015-04-19
draft:       false
promote:     true
sticky:      false
aliases:     [ node/460 ]
blog categories: [ "r" ]
flattr username: [ "nesono" ]

---

Another reminder of my classics. Sometimes, when you reduce data in a data frame some levels of categories are no longer contained in the observations after filtering but the factors still contain them in their levels.

To clean these up use the following command:

```r
cleanfactor <- as.factor(as.character(oldfactor))
```

That's it again. Cheers,  
iss

