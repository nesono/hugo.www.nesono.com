---
title:       "Matlab 7.5 (R2007b) & XQuartz 2.7.2"
type:        blog
date:        2012-08-13
changed:     2012-09-24
draft:       false
promote:     true
sticky:      false
aliases:     [ node/400 ]
blog categories: [ "admin", "matlab", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
After I had to upgrade the X11 support on OS X 10.8 (Mountain Lion), I got an annoying dialog asking for some strange application called *OroborOSX* every time I wanted to start Matlab.
After a quick look into the launch script, I found a solution and it seems to be aligned with Mathworks - the company behind Matlab.
<!--break-->

Simply open the file `/Applications/MATLAB_R2007b/bin/maci/StartMATLAB.app/Contents/launch_matlab.sh` in your favorite editor and go to line 8, where you should find something like the following listing:

	if [ "$?" != "0" ]; then
	  # The MathWorks does not officially support OroborOSX
	  # anymore, but since we used to, we will try to open it
	  # here for our MATLAB 6.5 users.
	  osascript -e 'tell application "OroborOSX" to activate'
	fi

And just comment out all these lines, so that all are preceeded by a `#`:


	#if [ "$?" != "0" ]; then
	#  # The MathWorks does not officially support OroborOSX
	#  # anymore, but since we used to, we will try to open it
	#  # here for our MATLAB 6.5 users.
	#  osascript -e 'tell application "OroborOSX" to activate'
	#fi

That's it, save and close the file and start Matlab again without the annoying dialog.
If you read the comment, you should be relieved by the fact, that we disabled starting an actually already abandoned service in this script.

Cheers,  
iss
