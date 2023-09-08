---
title:       "TIG - Git Curses Interface"
type:        blog
date:        2014-07-03
draft:       false
promote:     true
sticky:      false
aliases:     [ node/447 ]
blog categories: [ "os x", "shells", "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
Since some weeks, I am almost completely using `tig` for my work with git repositories.
It requires a unix shell and git to be installed (I have not tried to install it on windows) and I have found that the keyboard shortcuts need some tweaking.

The shortcuts are easy to remember and are particularly easy to use on a US layout keyboard (i.e., where `|`, `{}`, `[]`, etc. are easily avaialble).

 |     | **Standard Tasks**                               |
 | :-: | :----------------------------------------------: |
 | `=` | adds/removes files/changes from the index.       | 
 | `-` | discards changes in tracked file.                | 
 | `x` | deletes untracked files.                         | 
 | `<` | fetches the current state from the origin.       | 
 | `>` | pushes to the origin.                            | 
 | `|` | rebases the current branch                       | 
 | `{` | branches off (prompts for branch name)           | 
 | `}` | merges (prompts for branch to merge)             | 
 | `c` | commits verbosely (shows changes in editor)      | 
 | `+` | amends to last commit                            | 
 | `^` | pushes to stash                                  | 
 | `v` | pops from stash                                  | 
 | `[` | decrease diff context                            | 
 | `]` | increase diff context                            | 
 | `p` | cherry-pick a selected commit                    |
 
 |     | **Standard Views**                               |
 | :-: | :----------------------------------------------: |
 | `1` | main view                                        | 
 | `2` | status view                                      | 
 | `3` | view log                                         | 
 | `4` | tree view                                        | 
 | `5` | stash view                                       | 
 | `6` | grep view                                        | 
 | `l` | list branches (generic)                          |
 
 |     | **Small Helpers**                                |
 | :-: | :----------------------------------------------: |
 | `l` | graphical log for selected file (tree view only) | 
 | `r` | git ls-remote                                    | 
 | `P` | fetch all and prune                              | 
 | `y` | copy truncated hash to clipboard                 | 
 | `Y` | copy full hash to clipboard                      | 
 | `c` | checkout branch (branch view only)               | 

There are some small additional settings as well as some sensible defaults.
Check them using the `h` key.  
The full `tigrc` file can also be found on [github][1].  
Cheers,  
iss

[1]: https://github.com/nesono/nesono-bin/blob/master/tigrc
