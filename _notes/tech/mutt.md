---
title: Mutt for email
layout: tech
date: 2017-09-16
---
For quite a while I have enjoyed the command-line interface to the computer. And for a command-line interface to email, [mutt](https://mutt.org) is fantastic. It can be configured to talk to GMail and is very configurable.

As is the unix way, there are a number of ways of using mutt and an IMAP account (which Gmail offers as an access method). I have an initial configuration where mutt directly talks IMAP to Gmail and this works well, but is slowish as it talks back and forth.

So I did some digging and found Mutt+offlineimap+gmail <https://pbrisbin.com/posts/mutt_gmail_offlineimap/>. This setup syncs Gmail to a local sets of folders and you point mutt at that. It took a bit to configure and get initially synced up which was when I found an oddity in the folder naming. More digging and the above link is the older way that he does it, and he has moved on to using [isync](https://wiki.archlinux.org/index.php/Isync)

Some [discussion around the pros and cons of each](https://groups.google.com/forum/#!topic/mu-discuss/AhgmBAcv-ww)

The isync setup is light and fast. More configuration information can be found at <http://isync.sourceforge.net/mbsync.html>. An example dotfile <https://raw.githubusercontent.com/pbrisbin/dotfiles/v1.0/tag-mail-recipient/mbsyncrc>

This post helped to get the encryption settings right <http://irreal.org/blog/?p=6119>
### Notes

* The Mutt Guide <https://dev.mutt.org/trac/wiki/MuttGuide>
* The Mutt manual <http://www.mutt.org/doc/manual/>
* Understanding Folders <https://dev.mutt.org/trac/wiki/MuttGuide/Folders>
* Actions <https://dev.mutt.org/trac/wiki/MuttGuide/Actions>
* Patterns <https://dev.mutt.org/trac/wiki/PatternQuoting>
* Config <https://dev.mutt.org/trac/wiki/ConfigTricks>
* Mutt+GMail <https://dev.mutt.org/trac/wiki/UseCases/Gmail>
* Mutt+GMail on OSX <https://annvix.com/using_mutt_on_os_x>
* Some example configs <https://dev.mutt.org/trac/wiki/UserPages>
* isync/mbsync + systemd + notmuch <https://bostonenginerd.com/posts/notmuch-of-a-mail-setup-part-1-mbsync-msmtp-and-systemd/>
* using this setup to back up gmail <https://kevin.deldycke.com/2012/08/gmail-backup-mbsync/>
* alternative way to backup gmail <https://www.mattcutts.com/blog/backup-gmail-in-linux-with-getmail/> using [getmail](http://pyropus.ca/software/getmail/configuration.html)
* two ways to [forward an email](http://www.shallowsky.com/blog/linux/mutt-fwd-attachments.html)
