---
title:       "Migrating an SVN repository or: SourceForge Acknowledged Timecode4"
type:        blog
date:        2009-02-27
changed:     2012-10-15
draft:       false
promote:     true
sticky:      false
aliases:     [ node/197 ]
blog categories: [ "admin", "c/c++", "scm", "web" ]
flattr username: [ "nesono" ]

---

I need to migrate my local svn repository to sourceforge an therefore checked the web for such experiences once again. Recently, I found this [site][1], which has a neat trick for avoiding all these padding revisions from svndumpfilter. But let's keep it chronological. Here are the steps I took:


* Export the repository with svnadmin:  
```bash
svnadmin dump &gt; svn_export.dmp
```
* Filter out the paths I don't need in the new repository and drop empty revisions:  
```bash
cat svn_export.dmp | svndumpfilter --drop-empty-revs --renumber-revs include timecode4 > svn_clean_export.dmp
```
* Import the dump'ed data into the existing SourceForge repository  
```bash
svnadmin load < svn_clean_export.dmp
```

The two command line options for svndumpfilter basically did the job, which do not seem to be documented well.
Anyhow, I already migrated the svn repo once I started *nesono.com* and therefore, lots of empty padding revisions remained, but now you and I should now better.
And use the source for the next time ;)

The above technique is the best one, but I had no access to the actual file system on the target server, which you need for svnadmin. I did it that way:

* Export the source using `svn export` (see also `svn help export`), which simply exports the source without any svn data and imported the clean directory using `svn import`. This makes revision 1 the starting point

Cheers, admin

[1]: http://whynotwiki.com/How_I_moved_my_code_repository_to_Google_Code "moving to Google Code"
