---
title:       "Copy Current Filename and Line Number to Clipboard With Vim"
type:        blog
date:        2014-07-07
draft:       false
promote:     true
sticky:      false
aliases:     [ node/448 ]
blog categories: [ "freebsd", "linux", "os x", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I was working with a colleague and reasoned about some code over chat.
We sent filename and line number frequently and I got the impression that this is another perfect candidate for automation.
<!--break-->
Hence, I came up with the following solution, which can also be found on my .vimrc on [github][1].
Note that you need to check for the system vim is running on (linux/mac) or just pick the one line that matches your system.

<pre><code class="vim script">" mac version
nnoremap &lt;leader&gt;cfn :let @*=expand("%").":".line(".")
" linux version<CR>
nnoremap &lt;leader&gt;cfn :let @+=expand("%").":".line(".")<CR>
</code></pre>

That's it again,  
iss

[1]: https://github.com/nesono/nesono-bin/blob/master/vimrc
