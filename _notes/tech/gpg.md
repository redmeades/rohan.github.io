---
title: Implementing GnuPG
layout: tech
---
Whether you advocate for privacy or not, it is important to have a basic
understanding of cryptography in order to use modern digital technologies in
a secure manner.

One tool or standard that enables encryption is
[PGP](/wiki/Pretty_Good_Privacy) (Pretty Good Privacy) with its subsequent OpenPGP
standard. Due to some technical and philosophical issues, the original
implementation (PGP) was deemed inadequate and so the standard OpenPGP was developed. Gnu Privacy Guard is an implementation of this OpenPGP standard.

One of the common complaints: It is no for the faint-hearted.

* There is a [useful cheatsheet for common tasks](https://devhints.io/gnupg)
* The [GnuPG Manual](https://gnupg.org/documentation/manuals/gnupg/index.html)
* I have set up my keys using some of the settings and preferences [suggested in this post](https://dkg.fifthhorseman.net/blog/2019-dkg-openpgp-transition.html)
  
### notes

* A general purpose setup <https://security.stackexchange.com/questions/31594/what-is-a-good-general-purpose-gnupg-key-setup?noredirect=1&lq=1>
* Revision of advice above <https://dkg.fifthhorseman.net/blog/2021-dkg-openpgp-transition.html>
* Other <https://gpgtools.tenderapp.com/kb/how-to/first-steps-where-do-i-start-where-do-i-begin-setup-gpgtools-create-a-new-key-your-first-encrypted-email>
* should you store gpg passphrase in key manager? <https://duckduckgo.com/?q=should+store+gpg+phrase+in+password+manager&t=ffab&ia=web>
    - <https://www.reddit.com/r/ledgerwallet/comments/na31k5/storing_seed_phrases_on_a_password_manager/>
* Archive your PGP key <http://www.jabberwocky.com/software/paperkey/>
* If you forget… <https://medium.com/@fro_g/oh-no-i-forgot-my-pgp-private-keys-passphrase-6ec1d0228b48>
* Relation of GPG to password manager <https://security.stackexchange.com/questions/31989/is-gpg-suitable-as-part-of-a-password-manager-and-generator>
* And **Pass** that does this <https://www.thepolyglotdeveloper.com/2018/12/manage-passwords-gpg-command-line-pass/>

### subkeys

* Debian's docs <https://wiki.debian.org/Subkeys?action=show&redirect=subkeys>
* Advice on (sub)keys <https://security.stackexchange.com/questions/29851/how-many-openpgp-keys-should-i-make> = 1 key per identity, subkeys for devices and/or purposes

* 