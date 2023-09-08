---
title:       "Using LaTeX 'siunitx' Package With Version 1 and 2"
type:        blog
date:        2012-06-13
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/383 ]
blog categories: [ "latex" ]
flattr username: [ "nesono" ]

---

<!--more-->
I always forget how to configure [siunitx](http://ctan.org/pkg/siunitx) correctly in the preemble of a LaTeX document.
What makes it worse it that newer TeX distributions deliver version 2 while older distributions still use version 1 and both use different configuration variables.
If you use version 1, you'd probably want to use the following configuration:
<!--break-->

	% version 1 of siunitx package
	\usepackage{siunitx}
	\sisetup{per=fraction,fraction=nice,alsoload=binary,obeyall}

The setup configures `fraction` units to be printed using a fraction dash with superscript for nominator and subscript for denominator. The `binary` sub package loads bits and bytes units and `obeyall` makes inserted units inherit the font weight and font style of the context.

The same configuration for version 2 is as follows:

	% version 2 of siunitx package
	\usepackage{siunitx}
	\sisetup{per-mode=symbol,detect-all}
	\usepackage{xfrac}
	\sisetup{per-mode=fraction,fraction-function=\sfrac,alsoload=binary}

As a result of this mess I always insert both specifications and comment out the unused.  
Cheers,  
iss
