---
title:       "Broken Drupal View"
type:        blog
date:        2009-06-14
changed:     2012-10-04
draft:       false
promote:     true
sticky:      false
aliases:     [ node/237 ]
blog categories: [ "drupal" ]
flattr username: [ "nesono" ]

---

Today I stumbled over a problem using Views in Drupal. I had two listing Views - one listing all blogs, the other all posts, which muddled up my whole page: 

The navigation dropped to the bottom and the content was listed kind of hierarchical, but without following an obvious rule. I searched quite a while - made hundreds of queries to google, without success.

> The problem was caused by a teaser of a node, which opened a table, but did not close it. 

So be aware to provide self-contained teasers for each of your drupal posts, as they can mess up the whole page inside a view. You can use the button "Split summary at cursor" to tell drupal where the teaser should end. And don't forget to close any open tags before that ;)

Cheers, iss
