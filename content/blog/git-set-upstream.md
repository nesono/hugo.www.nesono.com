---
title:       "Git set upstream/tracking branch"
type:        blog
date:        2012-09-26
changed:     2012-11-07
draft:       false
promote:     true
sticky:      false
aliases:     [ node/409 ]
blog categories: [ "programming", "scm" ]
flattr username: [ "nesono" ]

---

<!--more-->
Again a nice [post][1] on stackoverflow - here's how to set the tracking or upstream branch `upstream` from remote name `origin` for a local branch `master`:
<!--break-->

<pre><code class="bash">git branch --set-upstream master origin/upstream</code></pre>

Cheerio,  
iss

[1]: http://stackoverflow.com/questions/520650/how-do-you-make-an-existing-git-branch-track-a-remote-branch "How do you make an existing git branch track a remote branch?"
