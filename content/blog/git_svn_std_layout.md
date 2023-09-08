---
title:       "git svn with standard layout and how to do a 'svn revert' with git"
type:        blog
date:        2009-04-29
changed:     2012-10-06
draft:       false
promote:     true
sticky:      false
aliases:     [ node/208 ]
blog categories: [ "programming", "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
In my last <a target="_top" href="http://www.nesono.com/node/207">blog</a> I made a recall on git, linking to a workflow example, presented by the <a target="_blank" href="http://www.gnome.org/">GNOME</a> guys. After some more days using git, I need to re-update ;)
<!--break-->

Starting with the "git svn clone" command. This command knows the option -s or --stdlayout, if an svn repository with a so-called standard layout shall be cloned. The standard layout is the directory structure of the repository or project. E.g. the project test_project needs to have the following structure

	test_project/
	  trunk/
	  tags/
	  branches/

To clone this project and preserve svn's tags and branches, use the following command

```bash
git svn clone -s http://svn.example.com/test_project
```

Additionally, after some coding, I needed something like a 'svn revert' and searched for it in git. I found this <a target="_blank" href="http://bryan-murdock.blogspot.com/2007/07/git-revert-is-not-equivalent-to-svn.html">site</a>, and boom, got the solution :) The following line will reset the changes in your working files.

```bash
git reset --hard HEAD
```

**AND NOT**

```bash
git revert HEAD
```

**which would revert your last commit - something not even possible with svn!**

If you want to reset a single file only, you should use the following command:

```bash
git checkout -- filename
```

You can leave out the '--'. They are just in case you have a file, which has the same name as a command or option of git.

Cheers, iss
