---
title:       "Disqus Module Broken"
type:        blog
date:        2015-10-10
draft:       false
promote:     true
sticky:      false
aliases:     [ node/470 ]
blog categories: [ "web", "drupal" ]
flattr username: [ "nesono" ]

---

My Disqus module did not seem to work any longer (the comments no longer showed up in the blog posts).
I fixed it hopefully by reinstalling the Disqus module, updating the *Libraries API* module to version 2.x (and then reconfiguring the Disqus module).

The error message in my http error log was:

```php
Call to undefined function libraries_detect()
```
Should work again now. That's it again  
iss
