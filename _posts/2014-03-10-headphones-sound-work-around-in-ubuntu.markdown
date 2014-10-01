---
layout: post
status: publish
published: true
title: Headphones Sound Work Around in Ubuntu
author:
  display_name: Udit Desai
  login: desaiuditd
  email: desaiuditd@gmail.com
  url: http://about.me/desaiuditd
author_login: desaiuditd
author_email: desaiuditd@gmail.com
author_url: http://about.me/desaiuditd
wordpress_id: 116
wordpress_url: http://blog.incognitech.in/?p=116
date: '2014-03-10 16:03:58 -0400'
date_gmt: '2014-03-10 10:18:58 -0400'
categories:
- Tech
tags:
- Ubuntu
- Headphones
- Speakers
comments: []
---

You might have faced this problem that your laptop speakers are working perfectly fine; but the same sound doesn't come when you attach your headphones to the laptop. Here's a small headphones sound work around in ubuntu:

1. Using a Terminal = "Applications->Accessories->Terminal"
2. Open this file for editing. `sudo vim /etc/modprobe.d/alsa-base.conf`
3. Insert this line at the bottom: `options snd-hda-intel model=hp-dv5 enable_msi=1`
4. Save. Close. Reboot. Check your levels in alsamixer. `alsamixer`
5. Press `<F6>` to select the correct sound-card. Press `<F3>` to show playback levels. `<F4>` selects capture levels [or use `<Tab>`]. Use the left/right arrow keys to select and up/down arrow keys to change levels. `<M>` to mute/unmute.
6. Go to "System ->Preferences ->Sound" and make sure the correct sound-card is default and adjust your profile on the hardware tab.
7. On the output tab choose the correct device.

And there you go !! Your headphones should be banging your ears with the bass ! :+1: :wink:

**NOTE :** This solution is tested on Ubuntu 13.04.
