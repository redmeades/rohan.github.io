---
title: 'Using PHP'
layout: tech
date: 2017-02-01
---
Notes on battling with PHP, lastest update on {{ page.date | date: "%b %d, %Y" }}.

### PHP + opcache

I ran into an issue whereby turning ON the opcache on PHP 5.6 would result in blank screens and request
failures in CiviCRM. 

* I came across [similar issues](http://civicrm.stackexchange.com/questions/3978/cannot-redeclare-class-crm-core-classloader-in-backup-site)
* and a civi [opcache issue](https://issues.civicrm.org/jira/browse/CRM-19781?jql=text%20~%20%22opcache%22)
* that pointed to [a php issue](https://bugs.php.net/bug.php?id=69090)
* Looking at the PHP opcache config yielded an odd, obscure and vague setting - [dups_fix](https://secure.php.net/manual/en/opcache.configuration.php#ini.opcache.dups_fix) - described as a 'hack'

Turning it on, seemed to have sorted out civi - I can turn on the opcache and not get the failures.

But after a while that didn't solve it seems :(

And the php-fpm process is throwing errors - "zend_mm_heap corrupted" and kill in the worker process.

More searching yielded [this stack conversation](http://stackoverflow.com/questions/2247977/what-does-zend-mm-heap-corrupted-mean). First answer was a maybe (but without rationale), but third one is worth a quick try.

Nope!

The second pointed to the [USE_ZEND_ALLOC=0]() [mentioned here](https://developers.oxwall.com/forum/topic/41865) and 
[various](https://bugs.php.net/bug.php?id=40479) [PHP](https://bugs.php.net/bug.php?id=58123) [issues](https://bugs.php.net/bug.php?id=70688) that speak about it.

Onto learning about [PHP memory management](https://jpauli.github.io/2014/07/02/php-memory.html) and finding a note that [you shouldn't do what is suggested](http://php.net/manual/en/internals2.memory.management.php)

More comments [mentioned disabling GC settings](http://php.net/manual/en/info.configuration.php#ini.zend.enable-gc)

This was also suggested by [this note](https://wiki.gandi.net/en/simple/errors/zend_mm_heap_corrupted) to do the same.

Eventually I found [two](https://github.com/oerdnj/deb.sury.org/issues/123) [reports](https://github.com/oerdnj/deb.sury.org/issues/128) about Debian PHP packages that suggested it had been dealt with. But which packages? So I decided to install the packages from this alternate repository on to a dev server.

**But** it seems that my regular update to Debian and a restart has resolved the issue - none of this was needed :(

Nope, wrong again.

After hours of working fine, the worker processes are crashing again :( but only on one of the servers.

So I have run diff on the 3 config files from the servers. There are a couple of differences in them, based on testing some of the suggestions above, so they are noted, but shouldn't be the issue.

And then I notices the php-fpm.conf has a difference in the [events.mechanism](http://php.net/manual/en/install.fpm.configuration.php) - 'epoll' was set on the server that is crashing. After some [reading up on the options](http://www.ulduzsoft.com/2014/01/select-poll-epoll-practical-difference-for-system-architects/) I commented the setting to go back to the default - I presume it is poll(), but could be select().

Stable again.

Next up will be to migrate CiviCRM back off the dev server.

* we adjusted VMs to relieve memory pressure, but this was on a different server to the one that initially had symptoms
* we kill a failing civi mailing that was aborting - maybe it was corrupting memory and killing the child process
* a [recent PHP bug](https://bugs.php.net/bug.php?id=73183) that is similar.
* this offers ['best opcache settings'](https://www.scalingphpbook.com/blog/2014/02/14/best-zend-opcache-settings.html)
* this is a great overview of [how the opcache handles memory](https://jpauli.github.io/2015/03/05/opcache.html)
* and some [fpm configuration](https://myjeeva.com/php-fpm-configuration-101.html) [suggestions](https://ma.ttias.be/a-better-way-to-run-php-fpm/)

### upgrading to ondrej-php

* following <https://github.com/oerdnj/deb.sury.org/wiki/PPA-migration-to-ppa:ondrej-php>
* and <https://medium.com/@federicopanini/update-php5-5-on-ubuntu-to-5-6-version-or-7-0-cb1370882faf#.6rzmozex9>
* upgrade to Jessie <https://linuxconfig.org/how-to-upgrade-debian-linux-system-from-wheezy-to-jessie-stable-release>
* use deb.sury.org builds of php <https://github.com/oerdnj/deb.sury.org/wiki/PPA-migration-to-ppa:ondrej-php>
* sudo vi /etc/apt/sources.list.d/php.list
* sudo wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
* sudo apt-get update
* sudo apt-get install php5.6-fpm
* sudo /etc/init.d/php5.6-fpm start
* edit to set listen 9000 - sudo vi /etc/php/5.6/fpm/pool.d/www.conf 
* check if fpm is running:  netstat -nlp|less
* check modules listing: php -m > /home/www/rohan/php-mods.hermas
* sudo apt-cache search php5.6
* sudo apt-get install php5.6-zip php5.6-xml php5.6-opcache php5.6-mysql php5.6-mbstring php5.6-intl php5.6-bz2 php5.6-curl php5.6-gd php5.6-json php5.6-ldap php5.6-mcrypt php5.6-soap php5.6-sqlite3 php5.6-xmlrpc php-memcache php-memcached
* sudo /etc/init.d/php5.6-fpm restart




