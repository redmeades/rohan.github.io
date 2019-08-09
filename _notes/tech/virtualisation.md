---
title: notes on various virtualisation approaches
layout: tech
---
We have been using VMware

* A usefule comparison of approaches and technologies <http://virt.kernelnewbies.org/TechComparison>

There are two major approaches (1) containers and (2) virtualisation

## Containers

### LXC

* LXC, LXD <https://linuxcontainers.org> - this aims at 'system containers' which are a full virtual environment, without multiple kernels and hardware simulation

### Docker

* [Docker](https://docker.com) - I have [some notes on our usage]({% link _notes/tech/docker.md %})
* Understanding the Docker Machine and Docker Engine <https://docs.docker.com/machine/overview://docs.docker.com/machine/overview/>
* You can run the engine on Linux, Windows and [on a Mac](https://docs.docker.com/docker-for-mac/)

### Virtualisation

Here both the hardware and operating system levels are virualised and presented
to the guest systems.

* VMware
* KVM

### KVM

* <https://wiki.debian.org/KVM>
* <https://doc.opensuse.org/documentation/leap/virtualization/html/book.virt/cha.kvm.intro.html>
* <http://www.dedoimedo.com/computers/kvm-intro.html>

## Putting it all together

* <https://www.servethehome.com/creating-the-ultimate-virtualization-and-container-setup-with-management-guis/>
* Part 2 <https://www.servethehome.com/setup-docker-on-proxmox-ve-using-zfs-storage/>
* <https://forums.servethehome.com/index.php?threads/proxmox-ve-5-0-and-docker-with-a-web-gui.13902/>
* <https://forum.proxmox.com/threads/docker-support-in-proxmox.27474/page-5>
