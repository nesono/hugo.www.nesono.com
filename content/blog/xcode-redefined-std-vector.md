---
title:       "XCode redefined std::vector<...>"
type:        blog
date:        2009-10-07
changed:     2012-10-02
draft:       false
promote:     true
sticky:      false
aliases:     [ node/258 ]
blog categories: [ "programming", "xcode", "c/c++" ]
flattr username: [ "nesono" ]

---

<!--more-->
Yesterday I stumbled over a problem using XCode 3. I was caused by a library, which was based on plain Makefiles. I tried to use this library in my XCode project, but anyhow, I always got the same error while linking.
<!--break-->

The object of a global function of the library could not be found, and the argument list showed a strange vector type:

<pre><code class="cpp">__gnu_debug_def::vector<...></code></pre>

Anyhow, after loads of investigation ;) I found two defines, set by XCode in debug mode:

<pre><code class="cpp">
_GLIBCXX_DEBUG=1
_GLIBCXX_DEBUG_PEDANTIC=1
</code></pre>

To fix it, I opened the project file inside the xcodeproj directory using a text editor and removed the lines with above defines. Afterwards, everything compiled and linked fine again :)

Cheers, iss
