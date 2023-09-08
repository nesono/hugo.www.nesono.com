---
title:       "Vim Packages for C/C++ Programming finally working - almost"
type:        blog
date:        2013-09-09
changed:     2013-10-21
draft:       false
promote:     true
sticky:      false
aliases:     [ node/438 ]
blog categories: [ "admin", "programming" ]
flattr username: [ "nesono" ]

---

<!--more-->
After my last trials with OmniCppComplete, exuberant-ctags, and similar vim plugins or packages I was really reluctant to restart this endeavor again and again with disappointment in the end.

While IDEs like Eclipse, Visual Studio, and XCode were getting stronger, my vim usage has degraded to plain text and short task single file editing where fewer magic was sufficient and the universal powers of vim most appropriate.
Even then, I was often drawn to editors like Sublime Text 2 due to features like multi cursor and plugins like emmet.
<!--break-->

Finally, my journey might have found an end! After reading [this blog about Vim autocomplete][1] on the web and watching a [screencast on youtube][2], I charged enough energy to give it another try.

I basically followed mostly [mentioned blog][1] with the exception that I am using [ultisnips][3] instead of [snip-mate][4] because it simply worked better for me. I installed the bundles using the excellent [pathogen][5], which also fits nicely with my dotfiles in my [github repo][6].  
In the end, I added the following bundles:

* [clang_complete][7]
* [SuperTab][8]
* [UltiSnips][3]
* [Syntastic][9]

I am using these extensions now for quite a while and except for highly sophisticated tasks and huge projects, everything runs fine out of the box. UltiSnips is actually turned out to be a killer feature - and is highly customisable.
The only flaw I have found is that `clang_complete` fails if the file path contains a white space character.

That's it again and cheers!  
iss

[1]: http://www.zwiener.org/vimautocomplete.html "Vim autocomplete"
[2]: http://www.youtube.com/watch?v=vk285Zc5_Zw "Using Vim and Tab"
[3]: https://github.com/SirVer/ultisnips "UltiSnips"
[4]: https://github.com/garbas/vim-snipmate "Snip-Mate"
[5]: https://github.com/tpope/vim-pathogen "Pathogen"
[6]: https://github.com/nesono/nesono-bin "nesono-bin"
[7]: https://github.com/Rip-Rip/clang_complete "Clang_Complete"
[8]: https://github.com/ervandew/supertab "SuperTab"
[9]: https://github.com/scrooloose/syntastic "Syntastic"
