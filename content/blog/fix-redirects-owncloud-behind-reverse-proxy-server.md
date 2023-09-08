---
title:       "Fix Redirects of OwnCloud Behind a Reverse Proxy Server"
type:        blog
date:        2015-10-09
draft:       false
promote:     true
sticky:      false
aliases:     [ node/468 ]
blog categories: [ "web", "freebsd" ]
flattr username: [ "nesono" ]

---

<!--more-->
I just fixed an issue that kept the OS X Contacts.app from synchronising with OwnCloud when running behind a reverse proxy.
For those who wonder, a reverse proxy is useful if you have a gateway http server that forwards http requests for web servers in a private network.
<!--break-->

First some details on my issue: I have several web servers running in (FreeBSD) jails that listen on loopback network devices.
The request coming into the host are forwarded by an nginx instance on the host to the specific jail (identified by the hostname).

For OS X Contacts, there are some redirects stated in the `.htaccess` file shipped with OwnCloud.
However, a redirect in the jail somehow inserts the loopback address into the HTTP request and since it's not a public accessible URL, the request failed.

The only viable solution for me was to move the redirects into the reverse proxy (nginx) so I ended up adding these statements to the site's reverse proxy configuration:

<pre><code class="conf"># rewrite rules are not working in the jail
rewrite ^/test$ /index.php last;
rewrite ^/\.well-known/host-meta$ /public.php?service=host-meta  last;
rewrite ^/\.well-known/host-meta\.json$ /public.php?service=host-meta-json  last;
rewrite ^/\.well-known/carddav$ /remote.php/carddav/  last;
rewrite ^/\.well-known/caldav$ /remote.php/caldav/  last;
rewrite ^/apps/calendar/caldav\.php$ remote.php/caldav/  last;
rewrite ^/apps/contacts/carddav\.php$ remote.php/carddav/  last;
rewrite ^/remote/(.*)$ remote.php  last;
rewrite ^/(build|tests|config|lib|3rdparty|templates)/.*$ -  last;
rewrite ^/(\.|autotest|occ|issue|indie|db_|console).*$ -  last;
</code></pre>

Note that you might have the proxy listening to both port `443` and port `8443` so you have to make sure it's active in both sections.

That's it again and cheers,  
iss
