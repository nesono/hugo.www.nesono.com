---
title:       "Matlab 7.5 GUI Slow Under Mac OS X"
type:        blog
date:        2011-01-28
changed:     2012-09-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/346 ]
blog categories: [ "programming", "matlab" ]
flattr username: [ "nesono" ]

---

<!--more-->
I know it's almost common sense, but today I had to refix the slow GUI for Matlab yet another time.
As the information seems to start vanishing from the web, I want to perpetuate it here.

Go into directory `/Applications/MATLAB_R2007b/bin/maci` (or wherever your installation resides) and create a file called `java.opts` with the following content.

	-Dapple.awt.graphics.UseQuartz=true

Cheers,  
iss
