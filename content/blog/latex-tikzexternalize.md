---
title:       "LaTeX tikz externalize to reduce memory usage and cache figures"
type:        blog
date:        2014-02-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/444 ]
blog categories: [ "latex" ]
flattr username: [ "nesono" ]

---

<!--more-->
A trick to reduce the memory usage of LaTeX (instead or in addition to increase LaTeX's memory as shown in [my previous post][1]) and to reduce build times for large documents with many tikz figures is to use `tikzexternalize`.
I add the following lines to my document definition:
<!--break-->

<pre><code class="tex">\usepackage{tikz}               % all my graphs and some hand tikz'd
\usetikzlibrary{patterns}
\usetikzlibrary{external}
\tikzexternalize[prefix=./]</code></pre>

Note that now many packets need to be wrapped into code that disables and re-enables externalising again, e.g., the `todo` package:

<pre><code class="tex">\newcommand{\xtodo}[2][]{\tikzexternaldisable\todo[#1]{#2}\tikzexternalenable}</code></pre>

or the missing figure command of the same package:

<pre><code class="tex">\newcommand{\xmissingfigure}[2][]{\tikzexternaldisable\missingfigure[#1]{#2}\tikzexternalenable}</code></pre>

Due to this side effect I would only recommend to use tikzexternalize when in urgent need, i.e., the document build times are unbearable.

That's it again!  
Cheers,  
iss

[1]: https://www.nesono.com/node/443 "LaTeX Tikz Main_memory Problems On OS X"
