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

<!--more-->
Another reminder of my classics. Sometimes, when you reduce data in a data frame some levels of categories are no longer contained in the observations after filtering but the factors still contain them in their levels.
<!--break-->

To clean these up use the following command:

<pre><code class="R">cleanfactor <- as.factor(as.character(oldfactor))</code></pre>

That's it again. Cheers,  
iss

