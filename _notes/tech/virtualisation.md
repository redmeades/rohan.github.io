---
title: notes on various virtualisation approaches
layout: tech
---
We have been using VMware

* A usefule comparison of approaches and technologies <http://virt.kernelnewbies.org/TechComparison>

There are two major approaches (1) containers and (2) virtualisation

### Containers

* LXC, LXD <https://linuxcontainers.org> - this aims at 'system containers' which are a full virtual environment, without multiple kernels and hardware simulation
* [Docker](https://docker.com) - I have [some notes on our usage](docker.html)

### Virtualisation

* VMware
* KVM

### KVM

* <https://wiki.debian.org/KVM>
* <https://doc.opensuse.org/documentation/leap/virtualization/html/book.virt/cha.kvm.intro.html>
* <http://www.dedoimedo.com/computers/kvm-intro.html>
