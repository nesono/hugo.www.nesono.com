---
title:       "Getting Win32 Vim Running with symbolic links for .vimrc and .vim/"
type:        blog
date:        2013-08-24
changed:     2013-08-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/436 ]
blog categories: [ "admin" ]
flattr username: [ "nesono" ]

---

<!--more-->
While my dotfile repository [nesono-bin][1] has been changed to run fine on Cygwin [recently][2], I suddenly had severe problems using Win32 [gvim][3].
Looking at the symptoms it became soon obvious that they were caused by the Cygwin-style symbolic link that was created by the nesono-bin installer script under Cygwin.

<!--break-->

The sad truth is that symbolic links from Cygwin are by no means file system level symbolic links but need to be expanded by the Cygwin shell to handle them correctly.
The only solution I have found is to install the [LinkShellExtension (LSE)][4], manually remove the Cygwin symbolic links (i.e., `~/.vimrc` and `~/.vim/`), and manually create the links pointing from `%HOME%\.vimrc` to `%HOME%\nesono-bin\vimrc` as well as from `%HOME%\.vim` to `%HOME%\nesono-bin\vim`.
Apart from that, I also had to do some additional checks in .vimrc, but then:
No more errors at startup like unreadable settings files - what a relieve!

LSE seems to support some more fancy stuff like Junctions, etc. so it's definitely worth a look.
So much for today,  
iss

[1]: https://github.com/nesono/nesono-bin
[2]: https://www.nesono.com/node/435
[3]: http://www.vim.org/download.php
[4]: http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html
