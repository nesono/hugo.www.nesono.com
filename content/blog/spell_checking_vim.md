---
title:       "Enable Spell Checking in VIM for Latex, etc."
type:        blog
date:        2010-06-03
changed:     2013-02-12
draft:       false
promote:     true
sticky:      false
aliases:     [ node/288 ]
blog categories: [ "operating systems", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
Yesterday, I needed to start spellchecking my latest paper and gave `:help spell` a try in vim.
The following line made me almost completely happy:
<pre><code class="vim">:setlocal spell spelllang=en_us</code></pre>

After that, typos were highlighted with respect to the alleged error made and suggestions are queried using `z=` for the word under the cursor or the selection in visual mode. 
Alternatively, the word can be added to the list of accepted words by pressing `zg`.

That's it, clean, small and simple :)  
Cheers,  
iss
