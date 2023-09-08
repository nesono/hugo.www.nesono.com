---
title:       "Add iptables Rules for Postfix to Support Ports 465 and 587"
type:        iss_doc_book
date:        2013-03-23
draft:       false
promote:     true
sticky:      false
aliases:     [ node/429 ]
flattr username: [ "nesono" ]

---

<!--more-->
As I could not convince `postfix` to listen to different ports than 25 for local mail delivery AND use `dovecote` as the LDA, I decided to add `iptables` rules to forward all incoming connections to standard ports 465 and 587 to my primary port 25.
Note that port 587 makes TLS mandatory and due to the fact that I suppress non-TLS I don't run into problems here.

<!-- break -->

As far as google nows, Ubuntu has no default configuration file for iptable rules. Therefore, I decided to add the rule set from scratch by hand (which was not difficult anyway). I simply added the following script to a new file `/etc/init.d/iptables`:

```bash

#!/usr/bin/env bash
# add redirect rules for ports 465 and 587 (to let postfix run on different ports)
iptables -t nat -A PREROUTING -p tcp --dport 465 -j REDIRECT --to-ports 25
iptables -t nat -A PREROUTING -p tcp --dport 587 -j REDIRECT --to-ports 25

```

Then, make the script executable:

```bash
sudo chmod 755 /etc/init.d/iptables
```

And finally add it to the startup rules:

```bash

cd /etc/rcS.d
ln -s ../init.d/iptables S60iptables

```

If you want to enable the rules without rebooting, simply call

```bash
/etc/init.d/iptables
```

That's it again.  
Cheers,  
iss
