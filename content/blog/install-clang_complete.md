---
title:       "Installing clang_complete using Pathogen"
type:        blog
date:        2013-08-31
changed:     2013-09-02
draft:       false
promote:     true
sticky:      false
aliases:     [ node/437 ]
blog categories: [ "admin", "c/c++", "linux", "os x", "ubuntu", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I installed clang_complete using [Pathogen][1] (i.e., I installed it as a submodule of my dotfiles git repository aka [nesono-bin][2].
I tried to be smart and went into the submodule's directory and invoked `make install`.
That nicely built the *vimball* and installed itself - but whenever I tried to open a `cpp`-file I got the following error:

```bash
"/tmp/sample.cpp" 10L, 144C
Error detected while processing function <SNR>15_ClangCompleteInit..<SNR>15_initClangCompletePython:
line   29:
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/Users/iss/nesono-bin/vim/bundle/clang_complete/plugin/libclang.py", line 63, in initClangComplete
    Config.set_compatibility_check(False)
  File "/Users/iss/nesono-bin/vim/plugin/clang/cindex.py", line 3126, in set_compatibility_check
    raise Exception("compatibility_check must be set before before " \
Exception: compatibility_check must be set before before using any other functionalities in libclang.
line   30:
E121: Undefined variable: l:res
E15: Invalid expression: l:res == 0
```

The error message was caused by the fact, that vim was loading `clang_complete` twice, as it was now installed in the `bundle` directory **and** in the `plugin` directory.  
To fix this issue, I deleted all `clang_complete` related files:

```bash
bin/
doc/clang_complete.txt
doc/tags
plugin/clang/
plugin/clang_complete.vim
plugin/libclang.py
plugin/snippets/
```

Everything worked pretty fine from now on.  
That's it again  
iss

[1]: https://github.com/tpope/vim-pathogen
[2]: https://github.com/nesono/nesono-bin
