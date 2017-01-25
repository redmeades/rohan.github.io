---
layout: guide
title: "Why text based formats are superior (for text-type information)"
permalink: /guides/text/
date: 2016-02-20
---
There are many reasons that I think that using text based formats for as much as possible
is vastly superior to other binary formats.

Firstly, by ‘text based formats’ I mean that one writes a document and that file can be seen
and edited in any one of a number of text editors on any platform, without a special piece 
of software.

There are a number of types of documents that you can write in plain old text - text oriented
documents like this article, or a more scholarly essay, music, configuration files, data,
graphs; all of which can be edited on tablets, phones, computers, by Windows, Macs, and Linux boxes.

## What you can do with your text documents

At this point we need to look at ‘the unix way’ by which I refer to a philosophy that all unix-based
operating systems work - (1) text based configurations and (2) lots of small, task-specific applications
and tools that do one thing well. Many of these tools have text as their input and just as
often have text as their output. Many manipulate that text and trasform it or produce something else
as a result of it.

What I mean by this is that I can take a text document such as this and input it into a
tool like [markdown](https://daringfireball.net/projects/markdown/) or [pandoc](http://pandoc.org)
and produce a html output. Or using pandoc I can take this same text and produce a pdf document from it.

Or with a minor tweak I can take this document and filter it through a tool that will
substitute all instences of ‘I’ with ‘I, Rohan’ and then produce a pdf. Tools such
as [sed](http://sed.sourceforge.net) make this quite straightforward and can achieve
much in [a single line](http://sed.sourceforge.net/sed1line.txt).
See this [introduction to Sed](https://www.digitalocean.com/community/tutorials/the-basics-of-using-the-sed-stream-editor-to-manipulate-text-in-linux)
for a taster.

If I have two copies of a configuration file in text I can simply ask the diff tool
to compare them and it will give me a line by line breakdown of all additions,
deletions and changes.

I can utilize the [git suite of tools](https://git-scm.com/) to provide versioning to
this document and track all changes to a series of documents in a repository. In fact,
this website is [actually a git repository](https://github.com/redmeades/redmeades.github.io/)
that has been filtered through a tool to produce the html that you now see when reading this.

## Scholarship and plain text

When I first started writing in an academic context I was using a Linux system[^cf1] and
the available tools for document editing were limited. I chose the reasonable
alternative to Microsoft Word - OpenOffice and got on writing.

Early on I realised that it would be useful to have some kind of bibliography tool to enter
in the details of the references that I was coming across and so I searched around and found
[Bibdesk](http://bibdesk.sourceforge.net/) which I’ve been using ever since. Bibdesk enabled
me to enter in the details, select the citation style and copy and paste the output into my
documents. Pretty good - anything to make it faster and more consistent is a win.

But as a curious person I saw that Bibdesk was a frontend to a bibtex database. And what
is that? So I entered the world of TeX. Maybe is was a little driven by procrastination, but I
was won over by the case for [WYSIWYM](http://en.wikipedia.org/wiki/WYSIWYM) and so moved my
writing environment to [LyX](http://www.lyx.org) which is a frontend to the TeX environment.
Effectively, I was writing in plain text and letting the computer do all the thinking:

> TeX is a typesetting language. Instead of visually formatting your text, you enter your
manuscript text intertwined with TeX commands in a plain text file. You then
run TeX to produce formatted output, such as a PDF file. Thus, in contrast
to standard word processors, your document is a separate file that does not
pretend to be a representation of the final typeset output, and so can be
easily edited and manipulated.[^cf2]

Not having to wrestle with formatting documents is extermely useful, you just get on and
write, text is text, paragraphs work, headings are headings, lists are lists - you tell the
computer what this unit of text is and it does the work to render it so. And 99% of the time
you get what you are after without any fuss or wrangling. And it looks fantastic. The pdf
output of the LaTeX process is just spot on print quality typesetting.


<https://kieranhealy.org/blog/archives/2014/01/23/plain-text/>

<http://programminghistorian.org/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown>

[^cf1]:I started on [Slackware](http://www.slackware.com/) around 1995, on 7 1.44Mb floppies
    from memory, then switched to [Debian](https://debian.org) around the time of the
    [Bo](https://wiki.debian.org/DebianBo) release. I’ve used Debian for Linux installations
    ever since.

[^cf2]:<https://www.tug.org/begin.html>

