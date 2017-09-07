---
title: Understanding and dealing with DNS
layout: tech
---
DNS is an integral part of the internet and some awareness of what it is and how it works is a useful skill in this online, connected world.

For the most part It Just Works(tm), and is taken care of by the applications that you use and your operating system. But when it goes wrong it can mean that a site appears offline or worse still you communicate with a fake verions of a site and get infected with something nasty.

## Browsers

Modern browsers implement a small caching mechanism so that they don't have to do a dns lookup for every component on a page, leading to 100s of queries per page. But the flipside of this is that your browser may load up or have old, stale data that you want to get rid of.

### Firefox

You can install [a DNS Flusher plugin](https://addons.mozilla.org/en-us/firefox/addon/dns-flusher/) to clear this cache or you can do the following to manually override the cache settings:

* <http://www.kahunaburger.com/2009/03/18/clear-dns-cache-in-firefox/>
* <http://ccm.net/faq/555-disabling-the-dns-cache-in-mozilla-firefox>
* <https://superuser.com/questions/737455/how-to-flush-dns-cache-in-firefox>

### Google Chrome

Like the manual settings for Firefox, Google allows you under the hood and you can manually flush the cache

* <https://w3guy.com/flush-delete-dns-cache-firefox-chrome/>
