---
layout: guide
title: "Notes on producing epub documents"
permalink: /guides/epub/
date: 2016-02-20
---
Our purpose here is to run through a process that will produce a standard
formatted epub with the minimum of effort.

## Basics ##

Probably the easiest way to write to content for your epub is to write in
[markdown](https://daringfireball.net/projects/markdown/), which I would
recommend as [text based formats are vastly superior](/guides/text/).

And probably the easiest way to generate an epub document from those those text
files is to use [pandoc](http://pandoc.org).

By using this combination, you get many powerful aspects of publishing to an epub file
built into the tools and their defaults.

[A useful list of tools for creating and editing epub
files)[http://www.daisy.org/daisypedia/tools-creating-epub-3-files]

### Frontmatter

In order to have a properly formed epub document, you will need to include some
information such as the author, title, licence, etc. This appears in the
frontmatter and metadata of the document. If you are using pandoc, you can read
up on it at <http://pandoc.org/README#epub-metadata>

## The niceties ##

### Page Numbers ###

One of the questions around the interface between old and new technology is that of page numbers. Should
an ebook need to have page numbers? Why? This is a [matter of debate](http://wiki.mobileread.com/wiki/Page_numbers)
For academic purposes, a mechanism to point to the source of an idea
or quotation is important, and so I would suggest that some kind of reference system is needed.

In the case of paper books that is the page number and the way in which you can get a page number into your epub
has been set out in the guidelines: http://www.idpf.org/accessibility/guidelines/content/xhtml/pagenum.php
