---
title:       "Linux Server for iCal and Apple Address Book"
type:        blog
date:        2010-09-22
changed:     2012-09-27
draft:       false
promote:     true
sticky:      false
aliases:     [ node/321 ]
blog categories: [ "admin", "operating systems", "linux", "os x" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I read about an [DAViCal][1] update, which is supposed to support the [CardDav][2] protocol, the native Apple Address Book protocol.
I started by creating an "Addressbook Principal" by Hand using the DAViCal web interface, as also explained in the [DAViCal Wiki][3] and set its name to 'contacts'.
The point is, that I can add a contact either on my phone or desktop and it syncs automatically.
No more need to synchronize devices by hand!
<!--break-->

Adding the address book to the iPhone was no problem at all. I started `Settings` -> `Add Account...` and under `Other` I have chosen CardDAV account using the following settings:

	Server: calendar.example.com:443/caldav.php/username/contacts/
	User Name: username
	Password: secret
	Description: some description

The most important field is the server setting with the port and path inline.
And please don't forget to use your server name instead as well as your user name and password ;)

To fill the address book, I configured the Apple Address Book on my stationary Mac using the following settings:

	Server: https://calendar.example.com:443/caldav.php/username/contacts/
	User Name: username
	Password: secret
	Description: some description

Again, substitute the server name, user name and password with your data (and skip the error message).
Now, you can fill your server hosted address book by drag & drop from your local address book.

That's it,  
iss

[1]: http://www.davical.org/ "davical web site"
[2]: http://datatracker.ietf.org/doc/draft-ietf-vcarddav-carddav/ "vcarddav RFC draft"
[3]: http://wiki.davical.org/w/CardDAV "carddav on daivcal"
