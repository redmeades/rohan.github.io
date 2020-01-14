---
title: Exploring Google Cloud
layout: tech
---

In light of the climate related issues that we are facing, I have begun to look
at one of the significant users of energy, and thus potential contributor to the
issue - cloud services.

Greenpeace have a [reportcard for
services](http://www.clickclean.org/australia/en/) that indicates which are
better. And [Google rates very well](https://cloud.google.com/sustainability/).
These are consumer-facing services, and importantly Netflix gets a 'D' as it is
hosted on AWS. Amazon who provide a significant amount of platform services,
along with Microsoft (and Apple) [historically have been
slow on clean energy](https://www.greenpeace.org.au/news/Apple-Amazon-Microsoft-choose-dirty-energy-to-power-growing-cloud/)
and [Amazon did not appear to have met previous
commitments](https://www.datacenterdynamics.com/news/amazon-breaking-its-renewable-energy-commitments-greenpeace-claims/).

Greenpeace have chosen to use Google over AWS for this reason. Although there
was an open letter and [commitment on Amazon's
part](https://siliconangle.com/2019/09/19/amazon-google-make-big-renewable-energy-commitments/) to address this.

Unrelated, but it also seems that Google's platform is [cheaper and quicker](https://kinsta.com/blog/google-cloud-hosting/)

### Initial notes

There are a variety of services - fully managed apps, storage, VMs, etc

The platform can be controlled via their [Google Cloud
SDK](https://cloud.google.com/sdk/docs/). One component for storage is
[gsutil](https://cloud.google.com/storage/docs/quickstart-gsutil) and through
this you can host a static site. One can also migrate from Heroku (which sits on
AWS) to their [Google Kubernetes
Engine](https://cloud.google.com/solutions/migrating-ruby-on-rails-apps-on-heroku-to-gke).

For Rails there are [a few options](https://cloud.google.com/ruby/rails/)
including a [flexible app environment like
Heroku](https://cloud.google.com/appengine/docs/the-appengine-environments).
