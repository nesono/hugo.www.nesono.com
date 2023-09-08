---
title:       "Issues Installing Calendar and Contacts after OwnCloud Upgrade"
type:        blog
date:        2015-10-09
draft:       false
promote:     true
sticky:      false
aliases:     [ node/469 ]
blog categories: [ "web" ]
flattr username: [ "nesono" ]

---

After I upgraded OwnCloud, I got the following error message when trying to enable the Calendar or Contacts plugins:

```console
cURL error 60: SSL certificate problem: unable to get local issuer certificate
```

The only way to get around this was to download the zip files from the [OwnCloud App Server][1] and enable them in the GUI or using the `php occ` command.

That's it again  
iss

[1]: https://apps.owncloud.com "OwnCloud App Server"
