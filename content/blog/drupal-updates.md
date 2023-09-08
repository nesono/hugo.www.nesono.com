---
title:       "Drupal Updates"
type:        blog
date:        2008-12-12
changed:     2012-09-30
draft:       false
promote:     true
sticky:      false
aliases:     [ node/90 ]
blog categories: [ "admin", "drupal" ]
flattr username: [ "nesono" ]

---

<!--more-->
> You can now find a drupal upgrade script on [github][1] and for [drupal modules installation][2]! 
> Beware that this script was written for my site setup and works for me, maybe not for you, as you have other site setups, etc. 
> I wrote it with respect to other setups though, but will never guarantee that :) If you are reluctant, try drush instead - though drush screwed my page up at least :/ 

Recently, I needed to upgrade my drupal installation and was quite surprised by the complexity of a drupal system update. Therefore, I sum up the steps necessary here, to simplify the process next time.
<!--break-->

1. Put site into maintenance mode (switch to garland?)
1. Backup database (mysql) -> use phpmyadmin (save in dedicated directory) with a template like `nesono.com_%Y-%m-%d`
1. Unpack drupal in `/var/` (will be e.g. in directory /var/drupal-6.11)
1. Copy stuff (check `settings.php` vs `default.settings.php` first!)
  1. `cp /var/www/sites/default/settings.php /var/drupal-6.11/sites/default/`
  1. `cp -r /var/www/tmp /var/drupal-6.11/`
  1. `cp -r /var/www/sites/default/files /var/drupal-6.11/sites/default/`
  1. `cp -r /var/www/sites/all/modules /var/drupal-6.11/sites/all/`
  1. `cp -r /var/www/sites/all/themes /var/drupal-6.11/sites/all/`
  1. `cp -r /var/www/sites/all/libraries /var/drupal-6.11/sites/all`
  1. `chown -R www-data:www-data /var/drupal-6.11`
1. stop apache
1. Move the new drupal directory to the document root
  1. `rm -rf www.bup`
  1. `mv www www.bup`
  1. `mv drupal-6.11 /var/www`
1. Run `update.php` within document root
  1. start apache
  1. `http://www.nesono.com/update.php`
1. Put site back online (deactivate maintenance mode again)

As a shortcut for steps 5 to 7.1, you can copy & paste the following line into your terminal:

<pre><code class="bash">/etc/init.d/apache2 stop && rm -rf www.bup && mv www www.bup && mv drupal-6.11 www && /etc/init.d/apache2 start</code></pre>

And boom! That's it.  
Cheers, iss

[1]: http://github.com/nesono/nesono-bin/blob/master/drupal_upgrade.sh
[2]: http://github.com/nesono/nesono-bin/blob/master/drupal_module_install.sh
