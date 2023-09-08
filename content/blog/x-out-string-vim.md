---
title:       "X-out a String in C/C++ Using Vim"
type:        blog
date:        2012-07-01
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/385 ]
blog categories: [ "programming", "c/c++" ]
flattr username: [ "nesono" ]

---

<!--more-->
Some time ago, I wanted to x-out all constant C-strings (characters within `"`) in a C-file and wondered how to do that with Vim.
E.g. when you want to cross out every character of a `Hello World` String like this:
<!--break-->

	/* before */
	printf( "Hello World\n" );
	/* after */
	printf( "XXXXXXXXXXXXX" );

Finally, also with the help of the Vim IRC channel we came to this regex:

	s/"\([^"]*\)"/\='"' . substitute(submatch(1),".","X","g") . '"'/gc

Pretty Funny, by mostly useless.  
Cheers,  
iss
