---
layout: post
status: publish
published: true
title: Skype Notification Sound Distorted in Ubuntu
author:
  display_name: Udit Desai
  login: desaiuditd
  email: desaiuditd@gmail.com
  url: http://about.me/desaiuditd
author_login: desaiuditd
author_email: desaiuditd@gmail.com
author_url: http://about.me/desaiuditd
wordpress_id: 257
wordpress_url: http://blog.incognitech.in/?p=257
date: '2014-07-17 17:21:29 -0400'
date_gmt: '2014-07-17 11:36:29 -0400'
categories:
- Tech
tags:
- Ubuntu
- skype
- Notification Sound
- Distorted sound
- Skype Notification Distorted
comments: []
---

It has been noticed and seems to be a common problem in Linux Community users that Skype doesn't get along well with Linux Distros. Recently I upgraded to Ubuntu 14.04 & I was sure enough that it's not going to be in peace for long. The very first problem I observed that the Skype notification sound distorted in Ubuntu when it played &amp; also the distortion continued unless I logged out or shut down the machine.

Here are simple steps to follow in order to fix this issue:

1. Open the file `/etc/pulse/default.pa` in your favorite text editor with root privileges. E.g., `sudo vim /etc/pulse/default.pa`
2. Search for the line : `load-module module-hal-detect`
3. Append `tsched=0` to the end. i.e., `load-module module-hal-detect tsched=0`
4. Restart pulse or just restart your machine & the distortion should be gone.
5. If you do not have a line with `load-module module-hal-detect` then search for the line: `load-module module-udev-detect`
6. Append `tsched=0` to the end. i.e., `load-module module-udev-detect tsched=0`. And then restart the machine.

**NOTE :** Not sure what the side effects are by disabling Glitch Free Audio; but hey, at least it doesn't bug you with its annoying sound anymore :wink: :smile:
