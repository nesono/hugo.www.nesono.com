---
title:       "Python minidom parse xml.gz File"
type:        blog
date:        2011-08-24
changed:     2012-09-26
draft:       false
promote:     true
sticky:      false
aliases:     [ node/365 ]
blog categories: [ "programming", "python" ]
flattr username: [ "nesono" ]

---

<!--more-->
To parse a gzipped xml file using the minidom parser in Python, one has two options: Either hand over the file object pointing to the xml file or hand over the full content as a string. As I thought it would be the more powerful variant in terms of efficiency, I chose to use the file object, given by gzip.open(). This works for the SAX parser, but fails for the minidom parser somehow. This is for sure a bug, but it persists over many versions and many operating systems (tried Linux and Mac).
<!--break-->

Thus, I changed my code to read the content of the file completely into memory first and parse the string afterwards. See also the following listing.

	import gzip
	from xml.dom.minidom import parse, parseString
	
	# open and read gzipped xml file
	infile = gzip.open( options.infile )
	content = infile.read()
	
	# parse xml file content
	dom = parseString( content )

That's it!  
Cheers,  
iss
