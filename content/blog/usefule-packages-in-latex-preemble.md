---
title:       "Useful Packages in the Preemble"
type:        iss_doc_book
date:        2012-12-05
changed:     2012-12-15
draft:       false
promote:     true
sticky:      false
aliases:     [ node/423 ]
flattr username: [ "nesono" ]

---

<!--more-->
Latex provides a wide variety of additional packages to extend it's functionality or simply to make some things more convenient, automatic, and simpler to maintain.The following table gives an overview of the packages I use in a daily fashion for scientific publications (apart from the standard packages).

<!--break-->
## microtype

This is a very subtile but nice package that optimizes the typography of the paper on micro-level, e.g. by character protrusion and font-expansion. Just add the package to the preamble and see the difference - best recognized using an updating PDF viewer like Skim.

## xfrac

When in text mode (not equations), xfrac enables you to create nice fractions in both text mode and math mode. xfrac defines the command `\sfrac`, which can be used as in `\sfrac{1}{2}`.

## siunitx

Package for nice formatted (si-)units in a consistent way. To show 48000 kHz, you can say: `\SI{48000}{\kilo\hertz}`. It not only formats the units nicely but also inserts thousands separators if desired and is heavily customizable. Anyhow, I am drifting away from using it these days, as it's a lot to write something like `\SI{128}{\kilo\bit\per\second}` in contrast to just `$128\,$kbps`.

## todonotes

Package for inserting TODO statements in nice colorful boxes - so that you won't forget to fix/remove them. To add a todo statement, use something like `\todo{Find better wording here}`.

## subfigure

Every once in a while, you might need subfigures in a paper. This package provides a nice solution for it, including enumeration of subfigures and references support. To add a subfigure, use something like this:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
\begin{figure}%
\centering
\subfigure[First.]{...}\qquad
\subfigure[Second figure.]{...}\\
\subfigure[Third.]{\label{3figs-c}...}%
\caption{Three subfigures.}
\label{3figs}
\end{figure}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## tikz

THE drawing markup for latex. It's easier than most other markups I have seen so far and important if you want to use R's tikz device (as described later). The figures generated with tikz integrate nicely into the document and look like being set with LaTeX. An example Markov Chain:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
\begin{tikzpicture}[node distance=20mm,
	state/.style={
	% The shape:
	circle,minimum size=8mm,rounded corners=3mm,
	% The rest
	draw=black}]
% draw the nodes
\path (0,0)  node (A) [state] {A}
      (4,0)  node (B) [state] {B}
      (2,1)  node (D) [state] {D}
      (2,-1) node (M) [state] {M};
% draw the transitions
\draw [->] (A) to [bend left=15] (D);
\draw [->] (D) to [bend left=15] (A);

\draw [->] (D) to [bend left=15] (B);
\draw [->] (B) to [bend left=15] (D);

\draw [->] (B) to [bend left=15] (M);
\draw [->] (M) to [bend left=15] (B);

\draw [->] (M) to [bend left=15] (A);
\draw [->] (A) to [bend left=15] (M);
\end{tikzpicture}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## algorithm2e

Not the easiest algorithm package, but maybe the most powerful. Strange syntax, really, but nice for Pseudocode. An example taken from the manual:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
\begin{algorithm}[H]
  \SetAlgoLined
  \KwData{this text}
  \KwResult{how to write algorithm with \LaTeX2e }
  initialization\;
  \While{not at end of this document}{
    read current\;
    \eIf{understand}{
      go to next section\;
      current section becomes this one\;
    }{
      go back to the beginning of current section\;
    }
  }
\caption{How to write algorithms}
\end{algorithm}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## listings

Package for code listings supporting different programming languages, like C/C++, Ruby, Octave, Python, etc. An example from the manual:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
\begin{lstlisting}
if (i<=0) then i := 1;
if (i>=0) then i := 0;
if (i<>0) then i := 0;
\end{lstlisting}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## booktabs

Very nice table formatting. Note that you might want to change the `arraystretch` for tables using `\renewcommand{\arraystretch}{1.2}` in your preamble. The package also adds new rules (i.e., horizontal lines) for top, bottom, and mid separators.
The following listing shows a simple example for a table using the booktabs package:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
\begin{tabular}{@{}llr@{}}
\toprule
\multicolumn{2}{c}{Item} \\
\cmidrule(r){1-2}
Animal & Description & Price (\$) \\
\midrule
Gnat      & per gram & 13.65 \\
          & each     &  0.01 \\
Gnu       & stuffed  & 92.50 \\
Emu       & stuffed  & 33.33 \\
Armadillo & frozen   & 8.99 \\
\bottomrule
\end{tabular}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## hyphenat

A package I use mostly for suppressing hyphenation in certain words. Can do more, as I've heard, but I don't use it. For example, to suppress hyphenation of the word curiosity use `\nohyphens{curiosity}`

## balance

Balances the columns (in a two column page) on the last page, so that they appear of equal length. Taken from the package manual:

> [Balancing two column layouts] is done with the command `\balance`, which should be issued somewhere in the text of what would be the first column of the last page without balanced columns. If it is issued too late, i.e., in the second column, then a warning message is printed that balancing may not take place.

## natbib

Another nice package, useful for advanced bibliography stuff is natbib, which supports different types of references i.e., `\citep` for a *parenthetical* citation and `\citet` for a *textual* one.

## acronym

When writing scientific papers, one often has to deal with tons of acronyms. Apart from simply writing down these acronyms in running text, there are several things to keep track of, i.e., using short or long form of acronym, writing it in full form (long and short) at first occurrence, not introducing typos, changing a custom acronym etc. To ease this pain, the acronym package can be used to define acronyms and refer to those using keys which will be expanded to the actual acronym in short, long (at first occurrence) or whatever desired form. For example, I define some acronyms in the beginning of my document (after `\begin{document}`) like this:

<pre><code class="tex">\acrodef{voip}[VoIP]{Voice over IP}
\acrodef{mos}[MOS]{Mean Opinion Score}</code></pre>

Which can then be used in  the text, e.g.:

<pre><code class="tex">...was not reflected in the \ac{MOS}, leading to...</code></pre>

You can explicitly use the short form and long form like this:

<pre><code class="tex">was not reflected in the \acs{MOS}, leading to</code></pre>

# Example LaTeX file

The following listing just concatenates all packages above and adds some configuration candy to it into the well-known preamble. You could use it as a template for new latex papers, etc.

	% specify your documentclass here [report|article|...]
	\documentclass[a4paper,final]{article}
	% \documentclass[a4paper,draft]{article}
	
	% for nicer tables
	\usepackage{booktabs}
	% use package
	\usepackage{graphicx}
	\usepackage{microtype}
	\usepackage{balance}
	
	% version 1 of siunitx package
	%\usepackage{siunitx}
	%\sisetup{per=fraction,fraction=nice,alsoload=binary,obeyall}
	% version 2 of siunitx package
	\usepackage{siunitx}
	\usepackage{xfrac}
	\sisetup{per-mode=fraction,fraction-function=\sfrac,alsoload=binary,detect-all}
	
	\usepackage{hyphenat}
	\usepackage{todonotes}
	\usepackage{subfigure}
	\usepackage{listings}
	\usepackage[ruled,vlined,linesnumbered]{algorithm2e}
	\usepackage[sort&compress]{natbib}
	\usepackage{acronym}
	
	\usepackage{tikz}
	\usetikzlibrary{
	    calc,trees,positioning,arrows,chains,shapes.geometric,%
	     decorations.pathreplacing,decorations.pathmorphing,shapes,%
	    matrix,shapes.symbols}
	% objectstyle1, objectstyle2, and important line are defined by personal preference
	\tikzset{%
	    objectstyle1/.style={rectangle,minimum size=6mm,%
	    rounded corners=1mm, draw=black, very thick, text centered},%
	    objectsyle2/.style={rectangle,minimum size=4mm,%
	    rounded corners=1mm, draw=black, thick, text centered},%
	    important line/.style={thick}%
	}
	
	% some settings for nicer tables
	\renewcommand{\arraystretch}{1.2}

The main matter of the document could then continue like that:

	\title{And Now for Something Completely Different}
	\author{Eric Idle}
	
	\begin{document}
	\maketitle
	
	Is your wife a...``goer''... eh? Know what I mean? Know what I mean? Nudge nudge.
	Nudge nudge! Know what I mean? Say no more...Know what I mean?
	
	\end{document}

Very small, very non-sense. To get an idea of how LaTeX works, simply copy above two sections into a text file and save it with the extension `.tex` into a new folder, we will also refer to as the project folder.  
Read on for further detail!
