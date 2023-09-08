---
title:       "Using xargs on OS X to rebuild all my tikzdevice images with Rscript"
type:        blog
date:        2014-01-15
draft:       false
promote:     true
sticky:      false
aliases:     [ node/442 ]
blog categories: [ "os x", "latex", "bash", "r" ]
flattr username: [ "nesono" ]

---

<!--more-->
The last update of R's tikzdevice (0.7.0) broke all my manually tuned graphs and now I have way too large margins, symbols and text sizes, etc.
Even though this update was actually a fix to the previously broken tikzdevice (it simply needed insane amount of margins compared to the other output devices due to fishy metrics), I had workarounds in each graph which I had to fix now - again - manually.

I knew I needed to rebuild all `tex` files from the corresponding `R` files and so was able run a simple but awesome script that accelerated the whole process a lot.
It boils down to the tip I got from [Munky Morgy][1], which finally made `xargs` on OS X work for me:

<pre><code class="bash">find . -regex '.*/[^_].*\.R' -print0 | xargs -0 -P 16 -I {} ./_callR.sh {}</code></pre>

This searches for all files ending with `.R` and not starting with an underscore below the current directory.
Files starting with underscore are include or helper files in my project, so I do not want to process those.

The script `_callR.sh` is simple as that:

<pre><code class="bash">Rscript $1 ${1%%.R}.tex</code></pre>

And in each `R` file, I use the first argument as my output file.
What a relief - now `latexmk` should take the leap and parallelise building of the `tex` sources. ;)

Cheers,  
iss

[1]: http://munkymorgy.blogspot.se/2009/02/using-xargs-on-mac-terminal.html "Munky Morgy"
