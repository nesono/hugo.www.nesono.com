---
title:       "Install Octave with Home Brew under Mac OS X"
type:        blog
date:        2011-06-27
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/356 ]
blog categories: [ "programming", "octave", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
To install <a href="http://www.gnu.org/software/octave/" target="_blank">GNU Octave</a>, an Open Source Matlab clone under Mac OS X, you will need to install fltk and GraphicsMagick as specific versions first. To do so, install both using the following commands:
<!--break-->

```bash
brew install --HEAD fltk
```
```bash
brew install --with-magick-plus-plus GraphicsMagick
```

Then, after installation has finished, you can proceed with the installation of GNU Octave as follows:

```bash
brew install octave
```

After that, I installed gnuplot as well (no, it's not in the dependency list), because fltk was somehow no longer available in octave after my last reboot. Just invoke the following to get gnuplot (takes a while):

```bash
brew install gnuplot
```

That's it again.  
Cheers,  
iss
