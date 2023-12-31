---
title:       "Matlab uint16 and uint32 Classes"
type:        blog
date:        2010-12-17
changed:     2012-09-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/345 ]
blog categories: [ "programming", "matlab" ]
flattr username: [ "nesono" ]

---

<!--more-->
As I am doing some of my evaluations in Matlab, I was curious if I can emulate the behaviour of `unsigned int`, `unsigned short` C-variables in Matlab.
However, they behave quite different! 
If you have a `uint16` variable, which has the value 65535 (the maximum it can take) and increment it, it remains at 65535.
No wrap around :/

Besides that, I gave `diff( uint16() )`, which shows a serious bug.
To reproduce: enter the following into your Matlab terminal:

```matlab
ext_seq = diff( uint16( [65530:65535, 0:5] ) )
```

And you will get:

```matlab
ans = 1 1 1 1 1 0 1 1 1 1 1
```

This means, that Matlab takes care of the wrap around, just in a wrong manner.
The same "bug" occurred for me with `uint32` and made me wonder, what Matlab is insinuating with this behavior.
If you should know, please drop a note here!

To get standard behavior at least where only one wrap around occurs, I simply wrote a for loop now with two variables, one containing the last seq-entry and the other containing the current seq-entry.
If the difference is smaller than -(2^16)/2, then I add 65535 to the result.

Cheers,  
iss
