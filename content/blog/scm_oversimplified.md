---
title:       "Source Code Management Matrix - A CVS, Subversion, and Git Reference Table"
type:        blog
date:        2012-12-14
changed:     2013-01-07
draft:       false
promote:     true
sticky:      false
aliases:     [ node/427 ]
blog categories: [ "programming", "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I had to check in into CVS after millions of years having passed since I last invoked `cvs` in a terminal. I was really surprised how much I forgot about the tool I was using on a daily basis, several million years ago. As I converted towards using Git mostly and need to use SVN occasionally I decided to make my own little SCM Matrix here, to remember just the basics. Of course, CVS, SVN, and Git work completely different and creating a repository in CVS has very little in common with creating a repository in Git. However, I assume the reader knows the basic concept of the three SCMs and just needs to remember the correct syntax to get the things done. Here we go:

|        | CVS                                                                | SVN                                                | Git                                                           |  
| ------ | ------------------------------------------------------------------ | -------------------------------------------------- | ------------------------------------------------------------- |  
| init   | `cvs -d /path/to/repo init`                                        | `svnadmin create /path/to/repo`                    | `git init`                                                    |  
| import | `cd /path/to/sources`</br>`cvs -d ... import projectname dev beta` | `svn import /path/to/sources file:///path/to/repo` | `cp -r /path/to/sources/* .`</br>`git add .`</br>`git commit` |  
| add    | `cvs add filename`                                                 | `svn add filename`                                 | `git add filename`                                            |  
| commit | `cvs commit`                                                       | `svn commit`                                       | `git commit`                                                  |  
| update | `cvs up`                                                           | `svn up`                                           | `git fetch`</br>`git merge`                                   |  
               

More details can be found in the man pages or using the command line help of the specific tool. Hope you find this one useful!  
iss
