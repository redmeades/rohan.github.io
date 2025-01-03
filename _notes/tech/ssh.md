---
title: SSH - The Secure Shell
layout: tech
---
I have spent a lot of time in a terminal, both locally for development and
writing and remotely for server administration.

SSH is awesome for you can do great things like port forwarding:

    ssh -fN -D 8080 user@server.com

This will map port 8080 locally so that all data sent to that port will be forwarded to the server and then propagated from there.

One issue is that connections to servers often timeout when I get pulled onto
other tasks (or distracted). You can fix that in your configuration:

    ServerAliveInterval 120

Adding this to your ~/.ssh/config and it will ping the connection every 120 seconds
to keep it open [via](https://bjornjohansen.no/ssh-timeout).
