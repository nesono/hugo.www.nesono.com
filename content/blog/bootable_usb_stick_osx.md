---
title:       "Creating a bootable USB Stick on Mac OS X from an ISO Image"
type:        blog
date:        2012-09-26
changed:     2015-02-15
draft:       false
promote:     true
sticky:      false
aliases:     [ node/408 ]
blog categories: [ "linux", "os x", "ubuntu", "unix", "admin" ]
flattr username: [ "nesono" ]

---

This is actually just a copy of an article from ubuntu.com, but they tend to move things around and I like to have short search times. Apart from that, this works for FreeBSD and even for Windows (tested with Windows 7) as well. Sorry for this this blatant plagiarism, but it might be also to your advantage ;)

One more note: If you want to create a bootable USB stick to be **used on a Mac/OS X**, do not forget to format the stick with Disk Utility to `HFS+` with a `GUID` partition table.

_In case you want to create a bootable USB stick for OS X Mavericks / OS X Yosemite, there exists a shortcut command (note to change the target disk folder accordingly):_

```bash
sudo /Applications/Install\ OS\ X\ Mavericks.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ OS\ X\ Mavericks.app --nointeraction
```

To create an USB stick for general usage:

Download the ISO image in question
```bash
wget http://somewhere.org/input.iso
```

Convert the ISO image using hdiutil
```bash
hdiutil convert -format UDRW -o output input.iso
```

Check the device number of your USB stick, e.g. by
```bash
diskutil list
```

Unmount the key without ejecting it with
```bash
diskutil unmountDisk /dev/diskN
```
  , where N is the device number acquired previously

Move the image onto the key using
```bash
sudo dd if=output.dmg of=/dev/rdiskN bs=1m
```  
Note that using `/dev/rdiskN` might be faster than `/dev/diskN` and bs=1m is required since `dd` would otherwise block forever.

Eject the key with
```bash
diskutil eject /dev/diskN
```

Mind the small changes from the original ;)
If you now want to start from the bootable USB key, leave it plugged in your Mac, reboot and press Alt/Option (⌥) before the Apple logo occurs.

Cheers,  
iss
