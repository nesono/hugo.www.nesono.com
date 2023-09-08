---
title:       "vim-figutive, wow"
type:        blog
date:        2015-08-10
draft:       true
promote:     true
sticky:      false
aliases:     [ node/467 ]

---

<!--more-->
Tim Pope makes awesome vim modules, they seem to overtake and particularly take away many pains and pieces that I had to either solve  in my own, ham-fisted terms (e.g. quick fix list browsing) or simply could never solve (vim-abolish).

However, the plugins are usually overwhelming because they are so feature rich. Hence, I wanted to record the most useful pieces first and subsequently introduce more sophisticated (but not not less useful) stuff later.

<!--break-->

The following table lists some fugitive commands starting with the most used ones:

| command     | description                    | example             |
| ----------- | ------------------------------ | ------------------- |
| `:Gwrite`   | add file / stage changes       | `:Gwrite [path]`    |
| `:Gread`    | checkout file /discard changes | `:Gread [revision]` |
| `:Gstatus`  | git status (interactive)       | `:Gstatus`          |
