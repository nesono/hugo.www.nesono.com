---
title:       "When You Can Not Paste Your Password into the Webform"
type:        blog
date:        2012-05-18
draft:       false
promote:     true
sticky:      false
aliases:     [ node/378 ]
blog categories: [ "html", "web" ]
flattr username: [ "nesono" ]

---

<!--more-->
Today I visited one of these web pages that try to increase your security by prohibiting pasting the password from the clipboard. As I use a password generator and like to have large passwords, typing the password by hand three times was no option for me. I searched the web for a solution and found nothing. Maybe I was just asking the wrong questions, but I don't mind. Here's my solution.
<!--break-->

With the web form opened in a modern browser (i.e. Chrome, Safari or Firefox) and an inspection tool installed (built-in with Chrome/Safari, provided with Firebug for Firefox), I was able to simply disable the pseudo security annoyance:

With the focus in the password text input, right click and choose `Inspect Element`. Then simply edit the appearing HTML and change `onpaste="return false;"` to `onpaste=""`. Be sure to repeat this for every entry element, but in general, there are no more than two of them.

That's it,  
iss
