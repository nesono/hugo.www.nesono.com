---
title:       "OMNeT++ 4.0 Tutorial using queuinglib under Mac OS X"
type:        blog
date:        2009-04-04
changed:     2012-10-07
draft:       false
promote:     true
sticky:      false
aliases:     [ node/204 ]
blog categories: [ "programming", "omnet++" ]
flattr username: [ "nesono" ]

---

<!--more-->
With my switch to University, recently, I had to think about the choice of a network simulation application and received some recommendations about OMNeT++. The first sentence on the [website](http://www.omnetpp.org/) did sound promising:

> OMNeT++ is a public-source, component-based, modular and open-architecture simulation environment with strong GUI support and an embeddable simulation kernel.
<!--break-->

So I downloaded the source from the [download site](http://www.omnetpp.org/filemgmt/viewcat.php?cid=2), followed the hints on [this site](http://www.omnetpp.org/pmwiki/index.php?n=Main.OSX), which helped me in configuration and compiling and invoked *omnetpp* in my open Terminal. I wanted to follow the steps taken by the [screen cast tutorial](http://www.omnest.com/webdemo/ide/demo.html).
Hence, I imported the sample code from within the `samples` directory and boom, the problems occur. I want to save you (and possibly the future me) a lot of time and give a step-by-step guide for doing everything right with OMNeT++ on Mac OS X with appropriate annotations for why to do it this way:

* **Download the source code** using [wget](http://www.gnu.org/software/wget/) or [Firefox](http://www.mozilla.com/en-US/). 
  Safari 4.0 beta added another `.tar` to the end of the file and seems to have crashed the file encoding.
  I wasn't even able to compile the sample code, which came with OMNeT++.
* **Unpack the code** into the destination directory, in which you want to have it installed (I used `/opt`, you might use `/usr/local`). 
  OMNeT++ will remember its build path and use it later for the DYLD_LIBRARY_PATH.
* **The sample library `queueinglib`** cannot be build on its own. 
  It depends on the `aloha` library, which must be imported along with the `queueinglib` code from your installation directory (e.g. `/opt/omnetpp-4.0/samples`).
  The funny thing is, that eclipse still builds the queueinglib - although not all object files are available and it looks like everything is alright, until you want to run the code.
  You will receive an error like this: `class queueinglib:Queue not declared using Define_Module(), ...`
* The rest of the tutorial has some ambiguities, as the time specifying fields now must have an `s` as a suffix. The remaining `.ini` file should look like the following lines:

~~~~
	[General]
	network = demo
	cmdenv-status-frequency = 500s
	eventlog-file = results/demo-${runnumber}.log
	record-eventlog = true
	sim-time-limit = 20000s
	**.source.interArrivalTime = 0
	**.source.numJobs = ${jobs=30,60}
	**.serviceTime = exponential(${serviceMean=1..3 step 1}s)
~~~~

You should particularly notice the additional 's' characters at the end of each time specification. Now the simulation should run fine and you should get very similar results as the tutorial :)

Cheers, iss
