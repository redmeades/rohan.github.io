---
title: Using APIs for fun and automation
layout: tech
---
I use the following services, and have started to use their APIs to access and manipulate (ie. manage) what they provide for me. Rather than manually logging into their websites and clicking through the settings, I can program my computer to talk to their servers and achieve the same thing, but in a quicker, more consistent (ie. automated) way.

* Name.com for DNS <https://www.name.com/api-docs/DNS>
* Cloudflare for protection <https://api.cloudflare.com/#getting-started-endpoints>
* Mailgun for email <https://documentation.mailgun.com/en/latest/api_reference.html>
* Github for code <https://developer.github.com/v3/>
* Moodle <https://docs.moodle.org/dev/Web_services> and <https://docs.moodle.org/dev/Web_service_API_functions>
* Pocket for 'read it later' articles <https://getpocket.com/developer/docs/v3/retrieve>
* Microsoft for Office365 <https://developer.microsoft.com/en-us/graph>

### Getting started (with Ruby)

* <https://www.ibm.com/developerworks/library/os-understand-rest-ruby/index.html> - A good introduction
* <http://mike.bailey.net.au/2011/02/json-with-ruby-and-rails/> - another introduction
* <https://github.com/rest-client/rest-client> - A simple way of sending requests and processing responses
* <https://github.com/typhoeus/typhoeus> - An alternate request handler
* <https://ruby-doc.org/stdlib-2.1.4/libdoc/json/rdoc/index.html> Data usually is presented in JSON, this is the Ruby library for that
* <https://readysteadycode.com/howto-extract-data-from-html-with-ruby>
* <http://www.nokogiri.org/tutorials/parsing_an_html_xml_document.html> - Nokogiri handles the parsing of html if you need to scrape or process data from websites
* [This post helped to get the authentication part working](https://www.krautcomputing.com/blog/2015/06/21/how-to-use-basic-authentication-with-the-ruby-rest-client-gem/)

### Notes on MoodleAPI

* Documentation entry point <https://docs.moodle.org/34/en/Web_services>
* And <https://docs.moodle.org/dev/Web_services>
* A list of functions <https://docs.moodle.org/dev/Web_service_API_functions>
* A client example <https://docs.moodle.org/dev/Creating_a_web_service_client>
* <https://tracker.moodle.org/browse/CONTRIB-3472>
* <https://moodle.org/mod/forum/discuss.php?d=215219#p938593>
* There's also a ruby wrapper/interface <https://github.com/getsmarter/moodle-api>
