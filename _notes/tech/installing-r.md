---
title: Notes on installing R and modules
layout: tech
---
R is a potent, open-source tool and environment for doing reporting, data and
statistical work including visualisations. I have [notes on using
R](using-r.html)

### Getting up and running

You can download the installer from the website or use [Homebrew](homebrew.html)
to install it.

* normal install https://www.r-bloggers.com/installing-r-on-os-x/
* homebrew https://www.r-bloggers.com/installing-r-on-os-x-100-homebrew-edition/
* older http://stackoverflow.com/questions/20457290/installing-r-with-homebrew

The basic package is a command-line application, but the installer comes with a
GUI. For an even more powerful environment one can install
[R-Studio](https://r-studio.org).

### RQDA

I am interested in using computers to analyse text and so I thought that
[RQDA](http://rqda.r-forge.r-project.org/) looked like a useful tool to do that
with.

But installing it is terribly painful.

There are the R packages that can be installed directly, or you can use the
[github version](https://github.com/Ronggui/RQDA)

The issue seems to be [RGtk2](http://www.ggobi.org/rgtk2/) not building against
X11/XQuartz correctly.

#### 1st approach: install older GTK w/X11

* download and install a GTK build with X11 from <http://r.research.att.com/>
* we now need to point various things to this framework, so in your .bashrc add

    export
    PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:/usr/X11/lib/pkgconfig:/Library/Frameworks/GTK+.framework/Resources/lib/pkgconfig"

and

    export
    LD_LIBRARY_PATH="/opt/X11/lib:/Library/Frameworks/GTK+.framework/Resources/lib"

* trying to build things against this fails to locate a gdk file, we we need to
  edit one of the pkg-config files:

    sudo vi
    /Library/Frameworks/GTK+.framework/Resources/lib/pkgconfig/gdk-x11-2.0.pc
    add -I/opt/X11/include

* build successful, we can then start building our R packages now.

    R CMD INSTALL RGtk2_2.20.31.tar.gz

* and it builds successfully, but doesn't load correctly, and so fails to
  install.

#### 2nd approach: wrangling Homebrew

The gist of the issue seemed to be that Homebrew's gtk was bulid with XQuartz in
mind rather than X11 **and** that RGtk2 was built against Gtk with X11 and not
Gtk with XQuartz.

It was [this seemingly irrelevant
post](https://apple.stackexchange.com/questions/205404/how-can-i-get-gdk-x11-3-0-on-os-x)
that put me on the path to solving this.

* first, Homebrew's cairo needs to be reinstalled with X11 support:

    brew uninstall --ignore-dependencies cairo brew install cairo --with-x11

* then we need to change the configuration of Homebrew to build Gtk2 as we want:

    brew edit gtk under 'def install', change --with-gdktarget to =x11 append
    "--with-x" to the list

* now build Gtk:

    brew install --build-from-source --verbose gtk

* now for the R packages

    R CMD INSTALL RGtk2_2.20.31.tar.gz R CMD INSTALL cairoDevice_2.24.tar.gz

* another failure, this time for igraph; but from
  <https://github.com/hadley/xml2/issues/127> we can

    cp /usr/bin/xml2-config to ~/bin/ (or maybe /use/local/bin) edit this
    xml2-config to make line 3 prefix=/usr

* more building...

    R CMD INSTALL igraph_1.0.1.tar.gz 

Complete! And as a bonus, this process also enables
[rattle](http://rattle.togaware.com) to install

#### Notes

* <https://gist.github.com/sebkopf/9405675>
* <http://stackoverflow.com/questions/15868860/r-3-0-and-gtk-rgtk2-error>
* <https://apple.stackexchange.com/questions/202501/how-to-install-rgtk2-on-os-x-10-10-5>
* <https://github.com/Homebrew/legacy-homebrew/issues/43290>
* a similar issue with building against X11
  <https://trac.macports.org/ticket/13429>
* [rattle](https://CRAN.R-project.org/package=rattle) is a similar tool which
  has a similar build failure, and this post goes through installing that
  <http://marcoghislanzoni.com/blog/2014/08/29/solved-installing-rattle-r-3-1-mac-os-x-10-9/>
* <http://stackoverflow.com/questions/11465258/xlib-h-not-found-when-building-graphviz-on-mac-os-x-10-8-mountain-lion>
