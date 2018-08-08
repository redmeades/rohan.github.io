---
title: "Administering Moodle"
ntype: tech
---
### advanced grading

I'm unsure whether I initally had turned off the permissions for advanced grading, but certainly to turn them back on is a pain.

You need to go into the permissions for the teacher role and make sure that the following are ticked/on:

* moodle/grade:managesharedforms
* moodle/grade:sharegradingforms
* moodle/grade:managegradingforms - this enabled the 'Grading Method' field when editing an assignment

### Setting up notifications

* Docs <https://docs.moodle.org/31/en/Mobile_app_notifications>
* Issue of no devices registering <https://moodle.org/mod/forum/discuss.php?d=323517>
* and a related bug <https://tracker.moodle.org/browse/MDLSITE-4369>
* leading to this curl issue <http://stackoverflow.com/questions/26452755/php-curl-with-nss-is-probably-using-sslv3-insted-of-tls-when-connecting-to-htt>
