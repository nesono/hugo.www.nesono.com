---
title:       "Referring to Git Remote Repositories"
type:        blog
date:        2012-09-19
changed:     2012-09-20
draft:       false
promote:     true
sticky:      false
aliases:     [ node/405 ]
blog categories: [ "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
You can specify git repositories in different ways, depending on the protocol you use.


## File System
* `/path/to/repo.git`  
* `file:///path/to/repo.git`

## Git native protocol
* `git://example.com/path/to/repo.git`
* `git://example.com/~user/path/to/repo.git`

## SSH connection
* `ssh://[user@]example.com[:port]/path/to/repo.git`
* `ssh://[user@]example.com/path/to/repo.git`
* `ssh://[user@]example.com/~user2/path/to/repo.git`
* `ssh://[user@]example.com/~/path/to/repo.git`

## SSH (short form - no port support)
* `[user@]example.com:/path/to/repo.git`
* `[user@]example.com:~user/path/to/repo.git`
* `[user@]example.com:path/to/repo.git`

## HTTP and HTTPS URL variants
* `http://example.com/path/to/repo.git`
* `https://example.com/path/to/repo.git`

## rsync protocol (highly discouraged)
* `rsync://example.com/path/to/repo.git`

For more information read the book [*Version Control with Git*][1] ;)  
Best,  
iss

[1]: http://www.amazon.com/Version-Control-Git-collaborative-development/dp/1449316387/ref=sr_1_1?ie=UTF8&qid=1348065329&sr=8-1&keywords=version+control+with+git "Version Control with Git on Amazon.com"
