---
title: Setting up two-factor authentication
layout: tech
---
You really need to be using two-factor authentication, particularly for key services such as email and file storage and key companies such as Microsoft, Google and Apple.

In addition to your password, two-factor authentication adds a second piece of information to be required for logging in to a service (hence two factors). What this looks like is that for a given service I will enter my username, my password and then be prompted for a one-time code. This code may be sent by SMS or retrieved from an app or other device.

This one-time code is set up on a second device, usually your phone, and is algorithmically generated and will expire after 1 minute.

Therefore, **while an attacker may have stolen your password to a service and possibly decrypted it, they cannot also generate the one-time key for that service and so cannot log in**.

Two-factor authentication is available for [Microsoft](https://support.microsoft.com/en-us/help/12408/microsoft-account-about-two-step-verification), [Google](https://support.google.com/accounts/answer/185839?hl=en), [Apple](https://support.apple.com/en-au/HT204915), [Github](https://help.github.com/articles/about-two-factor-authentication/), [Dropbox](https://www.dropbox.com/help/security/enable-two-step-verification), [Nextcloud](https://docs.nextcloud.com/server/11/user_manual/user_2fa.html)[^1], etc

**Before** you turn it on, you will need an app for your phone to 'capture' and then generate the one-time codes. Google offers its [Authenticator](https://support.google.com/accounts/answer/1066447?co=GENIE.Platform%3DAndroid&hl=en&oco=0), but then do you trust them with all of your codes? [Authy](https://authy.com/blog/authy-vs-google-authenticator/) is another [well regarded app](https://www.guidingtech.com/50036/ditch-google-authenticator-authy/), but some of its features make it less secure[^2]. The more secure solution would be one that you can check the source code for and so that is [why some recommend](https://www.reddit.com/r/privacy/comments/2q01bb/google_authenticator_vs_authy_vs_freeotp_what_do/) the open-source [freeOTP](https://freeotp.github.io).

An even better solution, as recommended in the Reddit thread is to use freeOTP and **also** capture the codes onto a second phone for backup purposes, hence removing the need to rely on Authy's syncing.

As a general approach to set it up, you will need to log into the service, locate the settings (often under security) and turn on two-factor authentication. When you turn this on a unique code will be generated and this is usually presented as a [QR code]() that you can simply scan in your app and all of the relevant details will be picked up and configured.

See the links above for examples of setting up those services.
- - -
[^1]: I have had problems logging into the iOS app after it was turned on. I use it for the administrative account (you are using separate admin and users accounts aren't you?)
[^2]: They offer to 'back up' your codes to their servers making things easier to sync between devices, but also provides another opportunity for baddies to get at them

