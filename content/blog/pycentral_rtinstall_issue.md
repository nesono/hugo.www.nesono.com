---
title:       "pycentral rtinstall: package python-setuptools: not overwriting local files"
type:        blog
date:        2009-08-13
changed:     2012-10-04
draft:       false
promote:     true
sticky:      false
aliases:     [ node/246 ]
blog categories: [ "ubuntu" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I fixed my ubuntu 8.10 installation, where above error occured, whenever I wanted to upgrade the system. It occured while upgrading the python2.5-minimal package.
<!--break-->

The failure originated from the python-setuptools and the following (simple) commands fixed it cleanly:

<pre><code class="bash">sudo dpkg -r python-setuptools
sudo apt-get install python-setuptools</code></pre>

Cheers, iss
