---
title:       "Install R with Home Brew under Mac OS X"
type:        blog
date:        2011-06-27
changed:     2015-10-09
draft:       false
promote:     true
sticky:      false
aliases:     [ node/355 ]
blog categories: [ "os x", "programming", "r" ]
flattr username: [ "nesono" ]

---

<!--more-->
After some years as a MacPorts user I decided to give home brew a try, which are advertising their package manager with the sentence "Homebrew — MacPorts driving you to drink? Try Homebrew!". 
The idea is not to build everything from scratch and create another software micro cosmos but to reuse existing Mac OS X abilities and save some space (as well as [cpu] time for updates). 
Sounds promising I thought and installed it according to the website's [description][1].

One of the first things I wanted to install was "The R Project for Statistical Computing". 
Anyhow, since home brew requires people to think a bit, it was not as straight forward as some MacPorts rules.
For R, we need to have a fortran compiler installed. I did this using the following command:

```bash
brew install gfortran
```

Brew would complain otherwise that no fortran compiler is installed and R installation would fail. 
After that, everything is ready already and we can proceed using:

```bash
brew install R
```

NB! You need to run this command first if you are on a recent OS X:

```bash
brew tap homebrew/science
```

That's it - no rocket science but nice to know in advance...  
Cheers,  
iss

[1]: http://mxcl.github.com/homebrew/ "Home Brew Home Page"
