---
title:       "Software RAID Problems under Mac OS X"
type:        blog
date:        2010-07-22
changed:     2012-09-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/302 ]
blog categories: [ "admin", "operating systems", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
From time to time, my software RAID 1 behaves ugly. After sleep periods for instance, it ejects and is no longer in sync.
Today, I read an [article][1] from Apple, which seems to address my problem.
They are using `diskutil` on the command line and it seems to provide more information about the RAID's status than the `Disk Utility` GUI.
It presents information like this.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
sudo diskutil checkRAID
AppleRAID sets (1 found)
====================================================================
Name:                 Backup
Unique ID:            0F11E679-27C7-4F05-BA57-1C7410EC048F
Type:                 Mirror
Status:               Online
Size:                 749.7 GB (749678166016 Bytes)
Rebuild:              automatic
Device Node:          disk4
--------------------------------------------------------------------
#   Device Node       UUID                                   Status
--------------------------------------------------------------------
0   disk3s2           D560FCB5-14FE-4838-8D97-A03CA6B387B9   Online
-   disk1s2           859CAE06-A75C-426C-944A-BBA5E28F6FDA   Spare
====================================================================
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note, that this output was produced after I cleaned up some stuff.
I had a non existent third disk for example, which was identified to be in the RAID set - the UUID was similar to the one of device `disk1s2`.
The entry `Rebuild` was set to `manual` before I invoked:

```bash
sudo diskutil appleRAID update AutoRebuild 1 disk4
```

The fact, that `disk1s2` has the status `Spare` still bugged me.
Hence, I removed the disk from the RAID set again using the following command:

```bash
diskutil appleRAID remove BD91D31E-E311-4980-B756-1E9343F6CEA7 0F11E679-27C7-4F05-BA57-1C7410EC048F
```

Then, I re-added the disk using the following command - note that you can no longer use the UUID, as the drive lost it:

```bash
diskutil appleRAID add member disk1s2 0F11E679-27C7-4F05-BA57-1C7410EC048F
```

Now, a three hour rebuild process has been initiated, for which end I am still waiting now ;)

Cheers,  
iss

[1]: http://support.apple.com/kb/HT3305 "Apple support article"
