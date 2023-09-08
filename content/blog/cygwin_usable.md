---
title:       "Configure Cygwin to be usable"
type:        blog
date:        2013-08-18
changed:     2013-08-20
draft:       false
promote:     true
sticky:      false
aliases:     [ node/432 ]
blog categories: [ "programming", "operating systems" ]
flattr username: [ "nesono" ]

---

<!--more-->
Since my current job forces me to work on Windows most of the time, I desperately tried to get any shell/terminal on Windows shell to the same level as all other *nix shells in the 20th century.
It turned out to be an endeavour but with a decently working bash in the end.

After trying [MinGW][1], [Cygwin][2], [MKS ToolKit][3], and supplementary terminal emulators like [Console2][4] and [ConEmu][5], I finally stuck with Cygwin.
The best terminal emulator (the application that runs the shell) for me is the `mintty.exe` that is shipped with Cygwin.
It supports copy paste (even though through weird short cuts), window resizing (yay!), terminal colors, and different terminal fonts - you see I became pretty frugal over time.

The key for me were the following steps:

* Make minimal Cygwin setup and install additional stuff separately (i.e., git, subversion, cmake, etc.)  
  *Why? Because installing both the Cygwin version and the separate installer causes strange problems*
* Setup keyboard short cuts etc. in `mintty.exe`  
  *Why? Because short cuts are the ohly way to stay sane, even if you copy using `Ctrl-Ins` and paste using `Shift-Ins`*
* Add additional stuff to system's `PATH` variable  
  *Why? Because I want to use the installed stuff from within Cygwin*
* Create startup batch scripts (see below)  
  *Why? Because I wanted to develop or at least build from within Cygwin*
* Install SP1 of VS2010  
  *Why? Because otherwise environment variables tmp and TMP make problems among other things*
* Clone and install [nesono-bin][6] from github  
  *Why? Because then I have colors, a good prompt, useful setup of bash and zsh (if I really want this), all my helper tools, history search backwards using `PageUp`, etc.)

And actually, that's it. So if you come from Linux, Mac or some other *nix system and you want to have a useful shell on Windows, don't search around like me. 
It will safe several years of your life just to stick with Cygwin and get it work on a minimal level.

## Startup batch scripts

The startup batch which is shipped with Cygwin script is located in `C:\cygwin\Cygwin.bat` if you used the default location for your installation and contains the following content:

<pre><code class="batch">@echo off

C:
chdir C:\cygwin\bin

bash --login -i</code></pre>

To have access to Visual Studio tools you need to create another batch script that loads the environment in Windows `cmd.exe` and then start your `mintty` session from there.

I am using the following construct for Visual Studio 2010 (which also includes the Azure SDK):

<pre><code class="batch">@echo off

echo "Loading Visual Studio environment..."
call "C:\Program Files (x86)\Microsoft Visual Studio 10.0\VC\vcvarsall.bat"
echo "...finished"

echo "Loading Azure environment..."
call "C:\Program Files\Microsoft SDKs\Windows Azure\.NET SDK\2012-10\bin\setenv.cmd"
echo "...finished"

set CC=cl
set CXX=cl

echo "Starting mintty..."
start C:\cygwin\bin\mintty.exe -i /Cygwin-Terminal.ico -
echo "...finished! Over and out :)"</code></pre>

Note that I also add CC and CXX environment variables.
I found this useful for some build systems, but may be optional and you decide to include them on your own :)

Now you should add start links e.g. in `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Cygwin` that point to the newly created batch files.
I create the links by copying and modifying the existing Cygwin link and renaming it.

That's it again,  
iss

[1]: http://www.mingw.org/
[2]: http://www.cygwin.com/
[3]: http://www.mkssoftware.com/products/
[4]: http://sourceforge.net/projects/console/
[5]: https://code.google.com/p/conemu-maximus5/
[6]: https://github.com/nesono/nesono-bin
