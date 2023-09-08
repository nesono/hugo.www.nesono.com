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
<p style="text-align: justify; ">If you want to get rid of messages with this subject sent by the amavis installation of your mailserver, you need to edit&nbsp;<span style="color: rgb(0, 51, 0); "><b>/etc/amavis/conf.d/20-debian_defaults</b></span>:</p>
<code lang="perl">$final_banned_destiny = D_REJECT;</code>
<p>Don't forget to restart you amavis service using</p>
<code lang="bash">sudo /etc/init.d/amavis restart</code>
<p>That's it! Cheers,<br />iss</p>
