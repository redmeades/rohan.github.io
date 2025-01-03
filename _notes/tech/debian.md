---
title: Using Debian
layout: tech
---
I have been running [Debian](https://debian.org) on my computers for nearly 20
years. It has a robust package management system and while it doesn't generally
offer the latest greatest in the Linux world, stability is a priority for me and
so this suits.

###

* List removed packages that still have configuration files left over (and would
  require purging)

> dpkg -l | awk '/^rc/ { print $2  }'

* and purge these files with

> apt purge ffmpeg

* sometimes two sources will provide a package, you can see the candidates via

> apt-cache policy ffmpeg

* and install a specific version with

> sudo apt install ffmpeg=7:3.2.14-1~deb9u1

### Custom kernel compilation

* http://newbiedoc.sourceforge.net/system/kernel-pkg.html
* http://kernel-handbook.alioth.debian.org/
* http://www.debian.org/doc/manuals/debian-faq/ch-kernel.en.html
* http://wiki.debian.org/DebianKernelCustomCompilation
