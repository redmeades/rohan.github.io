---
title: "ViM - my editor of choice"
layout: tech
date: 20190308
---
I've been coding and administering servers for quite a while now and early on I decide
to go with ViM as my editor and begin to learn the deep ways of it.

* Take the time to learn the basics
* Spend a bit of time trawling through other people's .vimrc file - you will learn a lot about what
  you can change and how things can be set up
* Use buffers <http://stackoverflow.com/questions/102384/using-vims-tabs-like-buffers>
* Consider using set of plugins that bring together a bunch of functionality - like [SPF13](http://vim.spf13.com/)

# One liners

When one downloads the 'citation entry and references' from the T & F journal sites, it produces
an 'illegal' bibtex document. This[^1] will fix up the entries:

```
%s/@article {,/\="@article{".line(".").","/
```

## links

* [quoting and unquoting words](https://stackoverflow.com/questions/2147875/what-vim-commands-can-be-used-to-quote-unquote-words)
* ViM [and splits](https://thoughtbot.com/blog/vim-splits-move-faster-and-more-naturally)

# installing/updating plugins

The plugin infrastructure for ViM is awesome, for spf13:

```
cd $HOME/.spf13-vim-3/
git pull
edit ~/.vimrc.bundles.local
vim +BundleInstall! +BundleClean +q
```

## Vimwiki

A useful plugin for writing text based notes is [vimwiki](http://vimwiki.github.io/).
I am adopting it based on [this post on taking
notes](https://jamesbvaughan.com/markdown-pandoc-notes/)

## Fugitive

This is a fantastic interface to [Git](). [Code](https://github.com/tpope/vim-fugitive) and [introduction](http://vimcasts.org/episodes/fugitive-vim---a-complement-to-command-line-git/)

## Advanced: folding

Vim has the ability to collapse (fold) and expand sections of the file to remove
them from view until they need to be looked at. You can find [a basic
introduction](https://www.linux.com/tutorials/vim-tips-folding-fun/).

[^1]: From <https://stackoverflow.com/questions/627932/vi-regular-expressions-replacing-using-current-line-number>

