---
title:       "Eclipse with PyDev under OS X Lion"
type:        blog
date:        2012-01-04
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/372 ]
blog categories: [ "programming", "python", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
Yesterday I wanted to start using the [Eclipse](http://www.eclipse.org/) extension [PyDev](http://pydev.org/), because I was tired of using the [pdb](http://docs.python.org/library/pdb.html) module.
Even more sophisticated debugging modules like [pudb](http://pypi.python.org/pypi/pudb) did not satisfy my need for intuitive and comfortable python debugging.
Even though I heard of the PyDev extension quite a while ago, I never gave it a try, as I was reluctant using the Eclipse Framework for Python.

As already said, yesterday I took comfort and installed PyDev in my local Eclipse installation using `Install New Software...` from the Help menu.
The installation process was finished in a wink and I could start my application right away using the `Run` button.

However, when trying to debug (using the bug symbol in the toolbar), I got the following error:

	ImportError: dlopen( /System/Library/Frameworks/Python.framework/Versions/2.6/lib/ python2.6/lib-dynload/math.so, 2): Symbol not found: __PyLong_AsScaledDouble

After consulting the all-knowing, all-seeing Trash Heap I found the bug mentioned on StackExchange and thought it might be worth sharing this information with you.

Here is how I fixed the problem: Open the Eclipse-Preferences (⌘-,), advance to PyDev -> Interpreter Python and remove the one configuration in the upper list of python interpreters. Then, install python from [home brew](http://mxcl.github.com/homebrew/) (or another source of choice) using:

	brew install python

and add the brew interpreter to Eclipse PyDev using the location `/usr/local/bin/python` and a name of your choice. For home brew's Python you might need to add `/usr/local/bin` before the occurrence of `/usr/bin` in your PATH variable as well as `/usr/local/share/python`.

After the proper installation of an alternative Python and it's addition to PyDev as the default interpreter, I was able to use PyDev smoothly and get back to work finally.

That's it!  
iss
