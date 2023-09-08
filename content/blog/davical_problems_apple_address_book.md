---
title:       "Davical Problems due to Apple Address Book Bug"
type:        blog
date:        2012-07-25
changed:     2012-09-24
draft:       false
promote:     true
sticky:      false
aliases:     [ node/397 ]
blog categories: [ "admin", "linux", "ubuntu" ]
flattr username: [ "nesono" ]

---

<!--more-->
I just added a workaround for [DAViCal][1] with Apple's Address Book application. Since my update to 10.7.4, I was no longer able to add a contact to the server and the card stopped the whole server communication to fail completely.

Looking at the apache logs showed me the following error:  
`[Mon Jul 23 11:54:16 2012] [error] [client 153.96.214.20] davical: LOG: :Response status 500 for POST /caldav.php/username/contacts/1101e8b5-071b-4b40-8293-b74d35264665.vcf`

After some additional research, I found this [thread][2] on the DAViCal list/forum - beware of the flame war side effects. Fortunately, Andrew himself answered and gave a neat patch - even though spread over different posts. So I'd like to sum up the solution here.

First, I opened the file `/usr/share/davical/inc/DAVResource.php`, jumped to line `1641` and added the following line

```php
case 'DAV::add-member':
  if ( ! $this->_is_collection ) return false;
  if ( isset($c->post_add_member) && $c->post_add_member === false ) return false;
  $reply->DAVElement( $prop, 'add-member', $reply->href(ConstructURL(DeconstructURL($this->url())).'?add-member') );
  break;
```

Then, you should add the following line to your `/etc/davical/calendar.example.com-conf.php`

```php 
// post member work around for Mac 10.7.4 - patch is in /usr/share/davical/inc/DAVResource.php:1641
$c->post_add_member = false;
```

And that's it.
Cheers,  
iss

[1]: http://davical.org/ "DAViCal"
[2]: http://www.gossamer-threads.com/lists/davical/general/2611 "Can't create contacts using Mac Address Book"
