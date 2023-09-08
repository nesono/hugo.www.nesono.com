---
title:       "<UL> Menu Right Aligned"
type:        blog
date:        2009-02-09
changed:     2012-07-10
draft:       false
promote:     true
sticky:      false
aliases:     [ node/190 ]
flattr username: [ "nesono" ]
blog categories: [ "programming", "html", "css" ]

---

<!--more-->
Today, I found a [website][1], which discussed the feature to make a `<ul>` (unordered list) based menu right aligned. To me, it was a bit confusing and I was not sure, what style items are necessary to get the work done. Now I can tell: Use the following two style declarations in the ul-section of your cascading style sheet.

* `display: table;`
* `text-align: right;`

And that's it :) Of course, you need to make sure, that your surrounding `<div>` etc. is big enough to be able to right align anything (per default, containers are as small, as their content and therefore would not right align it, as you might expect). And maybe, you can use `display: inline` in your `<li>` section... But thats up to you.

[1]: http://www.spartanicus.utvinternet.ie/left_and_right_alignment_using_css.htm "left and right alignment using CSS"
