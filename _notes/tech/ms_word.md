---
title: "Dealing with MS Word"
layout: tech
date: 2017-01-20
---
## Text blank ##

We had an issue with Word on Mac version 15.32 where opening a document presents you with a blank page, but the text is present, but 'hidden'.

Selecting the text and changing the font, or the font colour or the hidden attribute did not correct it.

But, switching to outline view and then back to print view forced the rendering of the text...

## AutoSave and Recovery ##

From <http://smallbusiness.chron.com/open-autosaved-asd-files-47094.html> we learn that there are a few
ways to see that Word has auto-saved a document for you - a 'recovery pane' is displayed when you open Word if
it detects a file. Or you can go to you recent files link and select a 'Recover files' link.

Auto-save files can be littered across the filesystem as .asd files. Double-clicking on them **does not** load
Word and trigger the recovery process, you have to associate them with Word first.

See <https://support.microsoft.com/en-us/help/107686/how-word-creates-and-recovers-the-autorecover-files> and
MS' advice on recovering at <https://support.microsoft.com/en-us/help/316951/how-to-recover-a-lost-word-document>

This [post on superuser](http://superuser.com/questions/896865/cant-open-asd-file) is also helpful.

## Word and links ##

So Word 2011 can't handle links to pdfs

* <https://answers.microsoft.com/en-us/msoffice/forum/msoffice_word-mso_mac/hyperlinks-are-very-slow-to-open-word-is-preparing/e3223cb7-2da2-40de-b754-fc8d58ae035e>
* <https://discussions.apple.com/thread/2733631?start=0&tstart=0>

And Word 2013 amd 2015 converts the '#' character in a URL, which is perfectly valid syntax, to '%20-%20' - breaking a document that we have written that links to many urls with anchors.

* <http://superuser.com/questions/596414/ms-word-2013-hyperlinks-with-anchor-tags-aka-hash-tags-bookmark-tags-to-ext>
* <http://stackoverflow.com/questions/25070176/hyperlink-changes-from-to-20-20-when-clicked-in-excel>
* <https://answers.microsoft.com/en-us/msoffice/forum/msoffice_word-mso_windows8/word-2013-hyperlink-converting-to-20-20/4e8a2e8d-b889-4c77-8276-551b11e296d4>
* Solution? Set default browser to IE (and possibly back to Chrome or Firefox) <http://stackoverflow.com/questions/17656083/excel-hyperlink-to-web-page-location-with-id-or-named-anchor>

### Export to PDF breaks hyperlinks

Using both the 'Save As...' and OSX's print to PDF functionality hyperlinks are lost in the output.

A possible solution, but not available on my edition. <http://superuser.com/questions/396143/how-to-export-from-word-to-pdf-without-losing-urls>
