---
title:       "OwnCloud SQLite is Only for Testing"
type:        blog
date:        2015-11-04
draft:       false
promote:     true
sticky:      false
aliases:     [ node/472 ]
blog categories: [ "web", "freebsd", "admin" ]
flattr username: [ "nesono" ]

---

<!--more-->
Lately I had to realise that the OwnCloud support for SQLite is literally only for testing, even if you have a single user, despite what I have read out of the documentation (which states you could use SQLite for few user sites).

I had several issues with my calendars as well as my contacts (failed to sync, failed to import, etc.), which all vanished when I migrated/converted the database to MySQL.
Luckily, OwnCloud has support for exactly that use case.
Just invoke the following (given you have setup php correctly).
<!--break-->

NB: it might be wise to put the server into maintenance mode and/or stop the web server while doing the conversion.

<pre><code class="bash">sudo -u www php occ db:convert-type --all-apps mysql <username> <host> <databasename></code></pre>

That's it again.
Cheers,  

iss
