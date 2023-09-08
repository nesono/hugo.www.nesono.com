---
title:       "Repair Time Machine after Computer Upgrade or Logic Board Fix"
type:        blog
date:        2009-06-17
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/238 ]
blog categories: [ "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
Some weeks ago, I got a new MacBookPro and installed the new system using my Time Machine backup disk - great feature!
After installation, it was the very same system, I was working at before - except for some minor changes (like the MAC address, etc).
Anyhow, Time Machine did not want to re-use the *old* Time Machine backups on my new laptop and hence started a new directory.
I left the old directory on my disk, even without being usable at all and today, I found a [page][1], which is coping with a very similar problem and adapted it to my situation.
<!--break-->

The basic steps are summarized in the following. 
The Time Machine backup disk is assumed to be called *Backup*.
The hostname is `MyMac`.
The old MAC address is `00:f9:e8:d7:c6:b5` and the new MAC address `00:1a:2b:3c:4f:56`.

1. Start the Terminal Application

1. Get the current MAC address using  
   `ifconfig en0 | grep ether`

1. Get the old MAC address by using  
   `cd /Volumes/Backup/Backups.backupdb`  
   `xattr -p com.apple.backupd.BackupMachineAddress MyMac`

1. Disable Time Machine in *System Preferences*

1. Disable ACL (access control list) using  
   `sudo fsaclctl -p /Volumes/Backup -d`

1. Move the old MAC address file to the new MAC address by  
   `sudo mv .00f9e8d7c6b56 .001a2b3c4f56`  
   Don't forget to change the MAC addresses to yours.

1. Write new MAC address to backup directory using  
   `sudo xattr -w com.apple.backupd.BackupMachineAddress 00:1a:2b:3c:4f:56 Backups.backupdb/MyMac`  
   Again, don't forget to change the MAC addresse to yours.

1. Move newly created backups into old directory, by  
   `sudo mv MyMac\ 2/* MyMac/`  
   The last command will result in a (harmless) error, which can be ignored. 
   You can now delete the old directory 'MyMac 2' in the Finder.

1. Re-enable ACL, using  
   `sudo fsaclctl -p /Volumes/Backup -e`

1. Eject and unplug the *Backup* disk

1. Re-Plug the *Backup* disk

1. Re-Start Time Machine (and possibly re-enable the Time Machine disk in Time Machine Preferences)

Unfortunately I have to note, that Time Machine will do a full backup after restarting.
I tried to follow the comments on above [site][1], but they all seem to be unrelated or even misleading - sorry.

Cheers,  
iss

[1]: http://www.macosxhints.com/article.php?story=20080128003716101 "10.5: Repair Time Machine after logic board changes"
