---
title:       "Write m-files for Matlab and Octave"
type:        blog
date:        2009-03-16
changed:     2012-10-15
draft:       false
promote:     true
sticky:      false
aliases:     [ node/200 ]
blog categories: [ "programming", "matlab", "octave" ]
flattr username: [ "nesono" ]

---

<!--more-->
Some days ago, I needed to write an m-file ([Matlab™][1] Function File), which had to run under [Octave][2] as well.
If you use full Octave compliant stuff, this works quite easily without modification of your code. 
But if you use e.g. subplot(...) with a range to make one plot broader or wider, Octave resigns. 
Therefore, I put in the following statement and wrote this blog message as a reminder :)
<!--break-->

	if exist('OCTAVE_VERSION')
	  figure
	else
	  subplot( 4,1,[2:4] )
	end

This runs under both, Matlab™ and Octave. Hope, this helped...

Cheers, iss

[1]: http://www.mathworks.com "Matlab Home Page"
[2]: http://www.gnu.org/software/octave/ "Octave Home Page"
