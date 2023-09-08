---
title:       "Batch Remove Tags in OS X Terminal"
type:        blog
date:        2015-10-17
draft:       false
promote:     true
sticky:      false
aliases:     [ node/471 ]
blog categories: [ "os x", "bash" ]
flattr username: [ "nesono" ]

---

<!--more-->
I just wanted to delete all tags set in my Applications folder on OS X and had to look up how to accomplish that in the Terminal since it a) is quite cumbersome to do it in Finder and b) it did not quite work somehow.

<!--break-->

The tags seem to be saved in the extended attributes `com.apple.FinderInfo` and `com.apple.metadata:_kMDItemUserTags`. For completeness, here is my complete "script":

<pre><code class="bash">cd /Applications
for file in *; do 
  echo $file; 
  sudo xattr -d com.apple.metadata:_kMDItemUserTags "$file"; 
  sudo xattr -d com.apple.FinderInfo "$file"; 
done
</code></pre>

That's it and Cheers,

iss
