---
title:       "Subversion, Mercurial and Git"
type:        blog
date:        2009-03-24
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/203 ]
blog categories: [ "programming", "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
Since I am working in very different environments (office, university, home) which do not always share access, especially towards the source code repositories, I searched for a feasible workflow using a distributed source code management like Mercurial or Git for my local work (on my laptop) and the base subversion repositories from the headquarters. I simply needed more history and would like to be able to commit things into a 'travel' intermediate repository while I am on the road and be able to check in the changes as soon as I have access to the base svn again.
<!--break-->

I started believing that <a href="http://www.selenic.com/mercurial/wiki/" target="_blank">mercurial</a> would be the system of choice, but its communication back to subversion seems to be non-mature at the time of this writing. This <a href="http://www.selenic.com/mercurial/wiki/index.cgi/WorkingWithSubversion" target="_blank">webpage</a> makes a nice comparison of the different approaches available for mercurial-svn workflows. Anyhow, the <a href="http://hgbook.red-bean.com/hgbook.html" target="_blank">book</a> is very nice and interesting. If I would need to start a new project with my source code management system of choice, I would probably choose mercurial. Especially the built-in **<a href="http://hgbook.red-bean.com/hgbookch12.html#x16-26700012" target="_blank">MQ</a>** extension looks really nice and seems to be very handy for people getting crazy with patches - maintainers maybe? ;)

After my short excursion on mercurial, I checked <a href="http://git-scm.com/" target="_blank">git</a> yet another time, although I am not a big fan of Torvald's polemic aggressions. Fortunately, it seems to do exactly, what I need - how ironic. As this <a href="http://jmibanez.livejournal.com/35264.html" target="_blank">blog</a> about an git-svn workflow describes:

	# clone the remote svn repository
	git svn clone https://svn.xxx.com/project localdir
	cd localdir
	
	# some available commands
	git status
	git diff
	git log
	
	# to visualize the repository's contents
	gitk --all
	
	# checkout of master and
	git checkout master
	#  'rebase' (pull changes from svn)
	git svn rebase
	
	# commit changes
	git commit -a -m'commit message' file.x
	git svn dcommit

That's it! :) It is essential to commit the change into your local git repo first along with the appropriate commit message. After that, the commits can be forwarded to the base svn repository, which seems to work as a glimpse :)

Cheers,  
iss
