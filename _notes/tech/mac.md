---
title: "Dealing with various things on a Mac"
layout: tech
---
LaunchCtl is used by macOS and homebrew also hooks into this to run background agents and services

> $sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist 
> $sudo launchctl unload  /System/Library/LaunchDaemons/ssh.plist

[^1]: <https://serverfault.com/questions/194832/how-to-start-stop-restart-launchd-services-from-the-command-line>
