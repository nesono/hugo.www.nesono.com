---
title:       "Move the Time Machine Backup Disk to a RAID 1"
type:        blog
date:        2009-06-05
changed:     2012-10-06
draft:       false
promote:     true
sticky:      false
aliases:     [ node/230 ]
blog categories: [ "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I was searching for an opportunity to move my existing Time Machine backup disk to a RAID system.
I wanted to create a RAID 1 by simply adding another drive to my existing backup drive and restore my old Time Machine data on the RAID, afterwards.
The following steps were accomplished with standard Mac OS X™ tools and can be performed for non-RAID systems as well.

## Create a backup of the old Time Machine disk

<div style="float: right"><a href="/sites/default/files/images/DiskUtilGathering.png" rel="shadowbox[gallery]" title="Disk Util Gathering"><img alt="" class="image" src="/sites/default/files/imagecache/thumbnail/images/DiskUtilGathering.png"></a></div>

1. Start `Disk Utility`.
1. Click on the old Time Machine backup disk.
1. Click on `New Image` in the tool bar.
1. Save the (compressed) image on another drive.

## Create the RAIDdevice

<div style="float: right"><a href="/sites/default/files/images/DiskUtilRaid.png" rel="shadowbox[gallery]" title="Disk Util RAID"><img alt="" class="image " src="/sites/default/files/imagecache/thumbnail/images/DiskUtilRaid.png"></a></div>

1. Go to the RAID tab.
1. Drag the two disks into the RAID area.
1. Name the RAID, I call it `Backup RAID`.
1. Click on `Create`.
1. The new RAID disk will appear on the left (restart Disk Utility).

## Scan Image
<div style="float: right"><a href="/sites/default/files/images/DiskUtilRestore.png" rel="shadowbox[gallery]" title="Disk Util Restore"><img alt="" class="image " src="/sites/default/files/imagecache/thumbnail/images/DiskUtilRestore.png"></a></div>
1. Select backup image in `Disk Utility`.
1. Select from menu `Images -> ScanImage for Restore`.
1. Wait a long long time.

## Restore Backup Data
1. Go to Restore tab
1. Drag your image to source.
1. Drag `Backup RAID` to destination.
1. Enable `Erase Destination`.
1. Click on `Restore`.

## Verify Backup RAID
<div style="float: right"><a href="/sites/default/files/images/DiskUtilVerify.png" rel="shadowbox[gallery]" title="Disk Util Verify"><img alt="" class="image " src="/sites/default/files/imagecache/thumbnail/images/DiskUtilVerify.png"></a></div>
1. Select `Backup RAID` on the left.
1. Go to First Aid tab.
1. Click on Verify Disk.

This should be it. Cheers,  
iss
