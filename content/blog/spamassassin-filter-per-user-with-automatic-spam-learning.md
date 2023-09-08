---
title:       "Spamassassin Filter Customized Per User With Automatic SPAM Learning"
type:        iss_doc_book
date:        2012-07-13
changed:     2017-11-23
draft:       false
promote:     true
sticky:      false
aliases:     [ node/391 ]
flattr username: [ "nesono" ]

---

<!--more-->
After obvious spam has been rejected before queuing using the Spamass-Milter, we can now proceed to check for spam specifically for each user.
The automation is based on each mail account having a `Junk` folder in its top directory - just as most mail clients already prepare at first start.
Note that the name of the folder is case-sensitive and you need the capital '`J`' if you use the following scripts and configuration entries.
<!--break-->

First of all, we need to maintain a separate spam database for each mail account.
I create a directory tree and populate the bayes database using the following script, saved as `spam_learn_mail_cron.sh` inside `/etc/cron.daily`.

	#!/bin/sh
	# script to create a directory under /vhome/users for each mail account,
	# populate the spam db with sa-learn, and fix the dir's permissions.
	
	# get all mail accounts
	for dir in /var/spool/postfix/virtual/*; do
	  mailaccount=${dir##*/}
	  echo "creating dir for $mailaccount"
	  spamdbpath=/vhome/users/${mailaccount}/spamassassin/
	  mkdir -p ${spamdbpath}
	
	  junkfolder=${dir}/.Junk
	  if [ -d ${junkfolder} ]; then
	    echo "learning spam from ${junkfolder} for user ${mailaccount}"
	    sa-learn --spam --dbpath ${spamdbpath}/bayes --progress ${junkfolder}
	    sa-learn --sync
	  else
	    echo "no Junk folder in top level - skipping"
	  fi
	
	  hamfolder=${dir}/.Archive
	  if [ -d ${hamfolder} ]; then
	    echo "learning ham from ${hamfolder} for user ${mailaccount}"
	    sa-learn --ham --dbpath ${spamdbpath}/bayes --progress ${hamfolder}
	    sa-learn --sync
	  else
	    echo "no Archive folder in top level - skipping"
	  fi
	done
	
	echo "fix permissions for whole vhome"
	chown -R vmail:mail /vhome
	chmod -R 700 /vhome

This script is automatically run every day, which should be frequent enough for most purposes.

Then, we need to configure spamd, which is done in the file `/etc/default/spamassassin`.
I simply change the `OPTIONS` variable to the following line.

	OPTIONS="--create-prefs --max-children 5 --helper-home-dir --virtual-config-dir=/vhome/users/%u/spamassassin -x -u vmail"

The option `virtual-config-dir` tells spamd to check for user databases in the virtual home directory tree instead of real user home directories.
The `x` and `u` options are mandatory for setting the `virtual-config-dir` and I set them to the appropriate values.

Now we need to tell postfix to use spamc and specify the name of the mail account for spamc invokation.
Therefore, I change the delivery agent line in `/etc/postfix/master.cf` to:

	# Dovecot LDA
	dovecot   unix  -       n       n       -       -       pipe
	  flags=DRhu user=vmail:mail argv=/usr/bin/spamc -u ${recipient} -e /usr/lib/dovecot/deliver -f ${sender} -d ${recipient}

Then don't forget to reload spamassassin, dovecot and postfix to enable the changes to the configuration files:

	/etc/init.d/spamassassin restart
	/etc/init.d/dovecot restart
	/etc/init.d/postfix restart

That's it again :)  
If you are unsure whether your setup really works, you should check the log using `tail -f /var/log/mail.info` and send yourself a message.

Cheers,  
iss
