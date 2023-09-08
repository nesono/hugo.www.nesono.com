---
title:       "Add Loopback Network Interface with Alias on FreeBSD"
type:        iss_doc_book
date:        2014-09-23
changed:     2015-05-03
draft:       false
promote:     true
sticky:      false
aliases:     [ node/451 ]
flattr username: [ "nesono" ]

---

<!--more-->
*Note that this page will be part of a documentation about setting up a server using FreeBSD with similar features to the existing server documentation. Also note that this page is still work in progress*

To use EzJail on a FreeBSD host, e.g. to sandbox different services, you need to add a loopback network interface and add some aliases to it. 
Jails networking seems to require a dedicated network and loopback aliases can not run on the external interface.
Follow the next paragraphs to add one loopback interface including three aliases.
<!--break-->  
First, create the loopback interface in `rc.conf`:
<pre><code class="bash">cloned_interfaces="lo1"</code></pre>

Then, add some aliases to the loopback interface in `rc.conf`:
<pre><code class="bash">ifconfig_lo1_alias0="inet 10.1.1.1 netmask 255.255.255.0"
ifconfig_lo1_alias1="inet 10.1.1.2 netmask 255.255.255.0"
ifconfig_lo1_alias1="inet 10.1.1.3 netmask 255.255.255.0"</code></pre>

If you happen to add an alias to an already running server, you might want to avoid rebooting and therefore also invoke the following command to add the alias while keeping the system running:
<pre><code class="bash">ifconfig lo1 alias 10.1.1.3 netmask 255.255.255.0 </code></pre>

That's it.  
iss
