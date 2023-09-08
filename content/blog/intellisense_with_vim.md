---
title:       "Intellisense with vim"
type:        blog
date:        2010-09-20
changed:     2012-09-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/320 ]
blog categories: [ "programming", "c/c++" ]
flattr username: [ "nesono" ]

---

<!--more-->
Since ever, I was searching for a solution for nice C++-aware code navigation for [vim][1].
The solution described here is based on

* [ctags][2]
* [omnicppcomplete][3]

Just install the omnicppcomplete plugin in vim and call ctags.

```bash
ctags -R --c++-kinds=+p --fields=+iaS --extra=+q ./
```

Invoke this call from the upmost working directory inside your project or give an appropriate path at the end of the command.

Cheers,  
iss

[1]: http://www.vim.org "vim homepage"
[2]: http://ctags.sourceforge.net/ "ctags on sourceforge"
[3]: http://www.vim.org/scripts/script.php?script_id=1520 "omnicppcomplete script page"
