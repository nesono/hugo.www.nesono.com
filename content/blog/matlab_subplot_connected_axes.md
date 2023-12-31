---
title:       "Matlab Subplot with linked/connected axes"
type:        blog
date:        2009-03-19
changed:     2012-09-24
draft:       false
promote:     true
sticky:      false
aliases:     [ node/202 ]
blog categories: [ "programming", "matlab", "octave" ]
flattr username: [ "nesono" ]

---

<!--more-->
I recently had to make a Matlab&trade; subplot and wanted to link the axes of the two plots together, so that both graphs show the same range on their x-axis.
Of course, there is a simple command for this in Matlab&trade;: linkaxes.
Detailed information about the command can be found on the <a target="_blank" href="http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/ref/zoom.html&amp;http://www.google.de/search?q=matlab+subplot+fix+zoom&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a">Web-Documentation</a>.
The following code shows, how I did it in my script.
<!--break-->

	ax(1) = subplot( 4,1,1 );
	plot(x)
	% ...
	ax(2) = subplot( 4,1,[2:4] );
	linkaxes(ax,'x');
	plot(u)
	% ...
	

It seems like, that the basic idea is to get the subplot handles (ax in the example) and connect the axes using linkaxes by specifying the subplot handle vector and the type of linkage (x,y,xy or off). As far as I 've seen, there are many ways to accomplish this task, but the above method seems to be the simplest to me.

Cheers, iss
