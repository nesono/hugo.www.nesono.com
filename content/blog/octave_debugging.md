---
title:       "Octave Debugging"
type:        blog
date:        2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/406 ]
blog categories: [ "programming", "octave" ]
flattr username: [ "nesono" ]

---

<!--more-->
*This was actually a Comment in another [post][1] of mine, but I'll paste it here since the migration to Disqus and it's worth a post anyway:*
<!--break-->

> iss replied on Mon, 2011-07-04 10:31:

I just found a nice site about Octave debugging. It told me about the following two functions, which are very nice for debugging, which is a pretty pitty in Octave in contrast to Matlab :/

	debug_on_warning(1)
	debug_on_error(1)

If you want to add a breakpoint to your function at a speciﬁc line, use the following statement

	dbstop('yourfunctionname',1)

Then you can use the dbxxx commands to debug your code:

	dbstep
	dbcont
	dbnext
	...

Happy debugging!  
iss

[1]: /node/356 "Install Octave With Home Brew Under Mac OS X"
