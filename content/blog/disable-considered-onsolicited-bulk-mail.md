---
title:       "Disable 'Considered UNSOLICITED BULK EMAIL, apparently from you'"
type:        iss_doc_book
date:        2010-07-25
changed:     2011-11-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/303 ]

---

If you want to get rid of messages with this subject sent by the amavis installation of your mailserver, you need to edit `/etc/amavis/conf.d/20-debian_defaults`

```perl
$final_banned_destiny = D_REJECT;
```

Don't forget to restart you amavis service using

```bash
sudo /etc/init.d/amavis restart
```

That's it! Cheers,  
iss
