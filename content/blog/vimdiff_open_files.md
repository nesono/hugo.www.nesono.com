---
title:       "Change to Vimdiff mode with two files open in a split view in vim"
type:        blog
date:        2014-09-03
draft:       false
promote:     true
sticky:      false
aliases:     [ node/449 ]
blog categories: [ "programming", "shells" ]
flattr username: [ "nesono" ]

---

Often I found myself starting an extra vimdiff session while I am actually working in another [vim][1] session. Finally, I took the time to search for a solution and I came up with the following two lines in my `.vimrc`:

```vim
nnoremap &lt;leader&gt;dt :windo diffthis<cr>
nnoremap &lt;leader&gt;do :windo diffo<cr>
```

They blindly go through all windows in the current view and enables or disable vimdiff, so use them with caution if you are a split view junky.

That's it,  
iss

[1]: http://www.vim.org (Vi IMproved)
