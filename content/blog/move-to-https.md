---
title:       "Moved to https Completely With Disqus and Chrome Issues"
type:        blog
date:        2012-06-29
changed:     2012-09-25
draft:       false
promote:     true
sticky:      false
aliases:     [ node/386 ]
flattr username: [ "nesono" ]
blog categories: [ "admin", "drupal", "web" ]

---

<!--more-->
Yesterday evening I decided to move from dynamic http/https switching to SSL (https) only mode. I decided to do so because I want everybody to feel free to take down her tin foil hats when visiting my site.
<!--break-->

For migration to SSL, I simply inserted the following rewrite rule into the apache configuration of the site:

	RewriteEngine On
	RewriteCond %{HTTPS} off 
	RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

However, I ran into several problems: First of all, [Disqus][1] had problems to view the comments under https. The only solution that worked for me was disabling the 2012 features of [Disqus][1] and therefore changing to the old fashioned interface.

More problems occur with the [Chrome Browser][2], which checks each SSL site for using non-SSL links or content. Unfortunately, Disqus Comments use non-SSL contents and therefore you'll get a warning each time you visit *nesono.com*. If you choose *Load Anyway* in the dialog, you'll get to see the comment numbers on the frontpage, if you choose *Don't Load (Recommended)*, you will not be able to read or write any comments here - and that's a pity!

Anyway, I hope this problem will be fixed soon - I think it has to be fixed in the Drupal Disqus module so that everything works as a charm again.

Best,  
iss

[1]: http://disqus.com "disqus"
[2]: http://www.google.com/chrome "Google Chrome"
