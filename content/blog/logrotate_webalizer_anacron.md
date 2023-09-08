---
title:       "Logrotate and Webalizer, Anacron"
type:        blog
date:        2009-02-24
changed:     2012-10-15
draft:       false
promote:     true
sticky:      false
aliases:     [ node/195 ]
blog categories: [ "admin", "operating systems", "linux", "os x", "ubuntu", "unix" ]
flattr username: [ "nesono" ]

---

<!--more-->
For nice usage statistics, I installed webalizer on my ubuntu server machine and enjoyed the nice diagrams after the first run. It was a bit suspicious, that the hits were such heavily increasing and so I decided to take a look on logrotate and furthermore crontab.

My server hosting provider seems to install anacron per default on his ubuntu standard installations, don't ask me why. Anyway, this disables standard cron usage. The second problem was, that anacron never has been started for weeks and so no logrotate or any other cronjob was cleanly running - yes, I laughed either, but maybe not as much as you.

After I deinstalled anacron (as it is NOT useful for always up and running machines), the reports in the webalizer html pages were very small, as they only covered one week maximum. I was searching some time for things like 'webalizer logrotate problem' or 'webalizer multiple log files', etc. in the web. Finally, I found a page, which praised the option '-p' of webalizer, which enables doing incremental updates of the statistics, without dropping the old stuff, so that it is not harmed logrotate.

For rebuilding the reports, I needed to concatenate all log files (in reversed order) into a big one, switch on 'Incremental' in the webalizer configuration file, set the big access.log file as the input file, remove the old data from the output directories and run webalizer with the following command on each config:

<pre><code class="bash">webalizer -c /etc/webalizer/site-webalizer.conf</code></pre>

Now the reports are refreshed and you should see positive feedback from webalizers standard output. After the update, you need to modify the LogFile entry in your site's webalizer config file to the first logrotate'd file (e.g. access.log.1), to have all webserver access included in the reports. I hope, that's it and if not, I will update this post... Cheers!
