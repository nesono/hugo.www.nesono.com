---
title:       "UTF-8 Graphics in iTerm"
type:        blog
date:        2014-07-02
draft:       false
promote:     true
sticky:      false
aliases:     [ node/446 ]
flattr username: [ "nesono" ]
blog categories: [ "os x", "shells" ]

---

<!--more-->
If you see strange symbols in [iTerm][1] when using [vim][2], especially with the [NERD Tree][3] and [Undo Tree][4], or in [tig][5], a super fast and flexible curses-based git interface, or simply when typing non ASCII characters in iTerm, you might want to add this to your shell config file (e.g., `~/.bashrc`, `~/.zshrc`, ...):
<!--break-->

<code class='bash'>export LC_ALL=en_US.UTF-8</code>

Do not forget to restart your shell!  
That's it,  
iss

[1]: http://www.iterm2.com/#/section/home
[2]: http://www.vim.org
[3]: https://github.com/scrooloose/nerdtree
[4]: https://github.com/mbbill/undotree
[5]: https://github.com/jonas/tig
