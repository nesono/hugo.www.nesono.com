---
title:       "Transferstack rewrite in Python"
type:        blog
date:        2013-08-19
draft:       false
promote:     true
sticky:      false
aliases:     [ node/402 ]
blog categories: [ "admin", "programming", "zsh", "bash", "operating systems", "linux", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
A long while ago, I re-wrote the transfer stack for the shell in Python.
The transfer stack is the counterpart to the directory dtack, which is known by the commands `pushd`, `popd`, and `dirs`.
The corresponding tools of the transfer stack are [`pusht`][2], [`popt`][3], and [`transfers`][4], all of which can be found in my [github][1] repository.
<!--break-->
While the directory stack is extremely useful for changing directories back and forth, the transfer stack has its strength when many files from different places should be collected in one or more destination directory.
The directory stack thereby supports both copying and moving files or directories from any source into any destination, as long as there exists a path.
It's functionality is very similar to the drop stack of [Path Finder][5]

With `pusht`, you can add files or directories to the stack, which should be moved or copied into some destination directory:

<pre><code class="bash">pusht mv fileA.txt cp dirA fileB.txt
cd some/where/else/
pusht cp fileC.txt dirB</code></pre>

The `transfers` command shows the contents of the Transfer Stack including information, if the file/directory should be moved or copied.

<pre><code class="bash">transfers</code></pre>

And with `popt` you can apply single or all stack actions or discard single or all stack actions.

<pre><code class="bash">popt -a</code></pre>

Before the re-write I had two versions of the transfer stack for bash and zsh, of which the zsh variant showed problems on OS X lately.
The new version is cleaner, simpler and should run on all unixes with Python (tested under 2.7) and in all shells, hopefully ;)

But check it out your self!

[1]: https://github.com/nesono/nesono-bin "nesono-bin GitHub Repository"
[2]: https://github.com/nesono/nesono-bin/blob/master/pusht "pusht"
[3]: https://github.com/nesono/nesono-bin/blob/master/popt "popt"
[4]: https://github.com/nesono/nesono-bin/blob/master/transfers "transfers"
[5]: http://www.cocoatech.com/pathfinder/
