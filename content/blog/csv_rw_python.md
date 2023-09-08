---
title:       "Read and Write CSV files with Python"
type:        blog
date:        2012-11-07
changed:     2015-02-08
draft:       false
promote:     true
sticky:      false
aliases:     [ node/414 ]
blog categories: [ "programming", "python" ]
flattr username: [ "nesono" ]

---

<!--more-->
Since CSV (comma-separated-values) files are supported by almost every statistics and/or math tool, I sticked to use the format for all my data collections.
<!--break-->
If you need further evidence, check out the (incomplete) list of natively CSV supporting applications:

* [Gnu/R][1]
* [KNIME][2]
* [MS Excel][3]
* [LibreOffice Calc][4]
* ...

Apart from those, a major benefit of CSV files is that you can edit them with any editor, as they are plain text files.
Unfortunately, some applications have poor support for such files, e.g. Matlab and Python.
Fortunately, as the file structure is so easy, you can add CSV support pretty easily.
In the following I will show you my solution for Python.

## Reading CSV Files with Python

The following snippet imports the CSV module and reads a CSV file including its header and data.

	import csv
	
	# open csv file
	csvfile = open( "inputfile.csv", "rb" )
	
	# sniff into 10KB of the file to check its dialect
	dialect = csv.Sniffer().sniff( csvfile.read( 10*1024 ) )
	csvfile.seek(0)
	
	# read csv file according to dialect
	reader = csv.reader( csvfile, dialect )
	
	# read header
	header = reader.next()
	
	# read data into memory
	data = [row for row in reader]
	
	# close input file
	csvfile.close()

## Writing CSV Files with Python

The following snippet writes a CSV file including its header and data.

	# open output file
	outfile = open( options.outfile, "wb" )
	
	# get a csv writer
	writer = csv.writer( outfile )
	
	# write header
	writer.writerow(header)
	
	# write data
	[ writer.writerow(x) for x in data ]
	
	# close file
	outfile.close()

That's it for now :)  
iss

[1]: http://www.r-project.org "The R Project for Statistical Computing"
[2]: http://www.knime.org "Konstanz Information Miner"
[3]: http://office.microsoft.com/en-us/excel/ "Microsoft Excel"
[4]: http://www.libreoffice.org/features/ "LibreOffice Calc"
