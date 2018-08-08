---
title: "Using Jekyll"
ntype: tech
---
Some notes on using Jekyll for a website.

### Using ###

By default, Jekyll uses [kramdown](https://kramdown.gettalong.org/) for its text to html conversion, so it is good to
have the [syntax chart](https://kramdown.gettalong.org/syntax.html) at hand.

### Hosting Jekyll ###

To [quote Jonas](https://www.quora.com/Which-are-the-best-web-hosts-for-Jekyll-based-sites/answer/Jonas-Mikka-Luster) - "I didn't bother screwing around with heroku or shotgun or a rack setup on Slicehost. Jekyll is about ease of use, didn't feel like complicating it down the line in deployment."

* [GitHub](https://pages.github.com/) is the standard
* the question has been asked [here](https://www.quora.com/Which-are-the-best-web-hosts-for-Jekyll-based-sites)
* Heroku - <https://www.garron.me/en/blog/deploy-host-jekyll-static-site-free-heroku.html>
* Google's Firebase - <https://desiredpersona.com/google-firebase-hosting-jekyll/>
* S3 - see [this gem](https://github.com/laurilehmijoki/jekyll-s3) renamed to [this gem](https://github.com/laurilehmijoki/s3_website) and [putting it together](https://www.maxmasnick.com/2012/01/21/jekyll_s3_cloudfront/)
* There's a hosting company, maybe, soon? <http://jekyllpress.com/>
* and these guys <https://www.netlify.com>

The S3 route is a [static site hosted by Amazon](https://aws.amazon.com/blogs/aws/host-your-static-website-on-amazon-s3/) available
