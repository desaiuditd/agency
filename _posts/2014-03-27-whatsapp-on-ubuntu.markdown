---
layout: post
status: publish
published: true
title: WhatsApp on Ubuntu
author:
  display_name: Udit Desai
  login: desaiuditd
  email: desaiuditd@gmail.com
  url: http://about.me/desaiuditd
author_login: desaiuditd
author_email: desaiuditd@gmail.com
author_url: http://about.me/desaiuditd
wordpress_id: 167
wordpress_url: http://blog.incognitech.in/?p=167
date: '2014-03-27 03:41:07 -0400'
date_gmt: '2014-03-26 21:56:07 -0400'
categories:
- Tech
tags:
- Ubuntu
- WhatsApp
comments:
- id: 6
  author: nicolas cuevas
  author_email: nicolascuevas@gmail.com
  author_url: ''
  date: '2014-07-25 21:14:00 -0400'
  date_gmt: '2014-07-25 15:29:00 -0400'
  content: nice post, i'll try it
- id: 7
  author: Udit Desai
  author_email: desaiuditd@gmail.com
  author_url: http://blog.incognitech.in
  date: '2014-07-31 02:19:00 -0400'
  date_gmt: '2014-07-30 20:34:00 -0400'
  content: |-
    Please do share your feedback. Let me know if you have any doubts.

    Happy to help. :)
- id: 8
  author: Azeez Abass
  author_email: blue-boy-cool@hotmail.com
  author_url: ''
  date: '2014-08-31 19:08:00 -0400'
  date_gmt: '2014-08-31 13:23:00 -0400'
  content: sweet! i was looking for the emojins
- id: 9
  author: DHEERENDRA PRASAD
  author_email: prasad.dheerendra@gmail.com
  author_url: ''
  date: '2014-09-20 18:49:00 -0400'
  date_gmt: '2014-09-20 13:04:00 -0400'
  content: I am getting server closed connection when I am filling all the details.
    Can you help on it?
- id: 10
  author: DHEERENDRA PRASAD
  author_email: prasad.dheerendra@gmail.com
  author_url: ''
  date: '2014-09-20 18:49:00 -0400'
  date_gmt: '2014-09-20 13:04:00 -0400'
  content: I am getting server closed connection when I am filling all the details.
    I am using elementary os luna which runs on ubuntu 12.04 LTS.
- id: 11
  author: Udit Desai
  author_email: desaiuditd@gmail.com
  author_url: http://blog.incognitech.in
  date: '2014-09-27 11:31:00 -0400'
  date_gmt: '2014-09-27 05:46:00 -0400'
  content: |-
    I'm really sorry, I do not have any knowledge on Luna.
    It maybe possible that WhatsApp has closed this loophole. Not sure though. Because I myself have stopped using this solution, as I've moved out from using WhatsApp itself :).
---

![](/uploads/2014/03/ubuntuwhatsapp2-257x266.png)

## Installation and configuration

1.  `apt-get install python python-dateutil python-argparse`
2.  `wget https://github.com/tgalal/yowsup/archive/master.zip`
3.  `unzip master.zip`
4.  `cd yowsup-master/src`
5.  `cp config.example yowsup-cli.config`
6.  `cat yowsup-cli.config`

        cc=34
        phone=34123456789
        id=
        password=

7.  `chmod +x yowsup-cli`
8.  `./yowsup-cli --requestcode sms --config yowsup-cli.config`

        status: sent
        retry_after: 3605
        length: 6
        method: sms

9.  `./yowsup-cli --register 123-456 --config yowsup-cli.config`

        status: ok
        kind: free
        pw: S1nBGCvZhb6TBQrbm2sQCfSLkXM=
        price: 0,89
        price_expiration: 1362803446
        currency: EUR
        cost: 0.89
        expiration: 1391344106
        login: 34123456789
        type: new

10. Copy the `pw` field from the output & paste it in front of `password` field in the `yowsup-cli.config`. Your `yowsup-cli.config` should look like below: `cat yowsup-cli.config`

        cc=34
        phone=34123456789
        id=
        password=S1nBGCvZhb6TBQrbm2sQCfSLkXM=

## Send a message

`./yowsup-cli --send 34111222333 "Test message" --wait --config yowsup-cli.config`

    Connecting to c.whatsapp.net
    Authed 34123456789
    Sent message
    Got sent receipt

## Receive messages

`./yowsup-cli --listen --autoack --keepalive --config yowsup-cli.config`

    Connecting to c.whatsapp.net
    Authed 34123456789
    34111222333@s.whatsapp.net [02-02-2013 14:14]:I have received a test message from you

## Interactive: Send and receive messages

`./yowsup-cli --interactive 34111222333 --wait --autoack --keepalive --config yowsup-cli.config`

    Connecting to c.whatsapp.net
    Authed 34123456789
    Starting Interactive chat with 34111222333
    Enter Message or command: (/available, /lastseen, /unavailable)
    Yes, I know it
    34123456789 [02-02-2013 14:15]:Yes, I know it
    Enter Message or command: (/available, /lastseen, /unavailable)
    34111222333@s.whatsapp.net [02-02-2013 14:16]:What are you doing?
    Enter Message or command: (/available, /lastseen, /unavailable)
    Testing a new application
    34123456789 [02-02-2013 14:16]:Testing a new application
    Enter Message or command: (/available, /lastseen, /unavailable)
    /unavailable

## Too much of geeky stuff ??

1. Skip all the steps of sending and receiving a message. Just install the WhatsApp client & configure it as mentioned.
2. We will use Pidgin Instant Messenger to make this work. Install it if you don't have it.
`sudo apt-get install pidgin`
3. Then install WhatsApp protocol implementation for Pidgin.
    - `sudo add-apt-repository ppa:whatsapp-purple/ppa`
    - `sudo apt-get update`
    - `sudo apt-get install pidgin-whatsapp`
4. Now simply launch Pidgin. Add a whatsapp account, put username as the phone number with country code (as written above) and password as the string we obtained earlier.
5. Use WhatsApp on Ubuntu of yours. ( **NOTE :** Don't use it simultaneously on your mobile ).

## WhatsApp Emojis for Pidgin

You need to install and enable the **Emoji smiley theme**. Just copy one of the sub-directories from following Git repositories to `$HOME/.purple/smileys/` and enable the newly installed theme in the Pidgin preferences window.

- [https://github.com/stv0g/unicode-emoji](https://github.com/stv0g/unicode-emoji)
- [https://github.com/VxJasonxV/emoji-for-pidgin](https://github.com/VxJasonxV/emoji-for-pidgin)

## Known Issues

I've tested this on my Ubuntu 13.04 (64 bit) & it seems to be working perfectly. Though the trouble part is at the other hand. Whenever the other person receives a message sent by us via Pidgin; the mobile phone hangs up a bit & WhatsApp gets crashed :wink: :stuck_out_tongue:

Yet, it's all togather a different story whether WhatsApp mobile app is reading messages properly  which comes from Pidgin or not. Maybe Pidgin seems to be sending any unknown message/socket headers which the mobile app can't decode. (Tested on Samsung S Advance & Micromax Canvas) Anyway, this problem is for the mobile users :stuck_out_tongue: and not for you if you want to use WhatsApp on your machine.

Regarding Emojis, some of them might not work but this is the best that I've come across.

**NOTE :** This method will not work if you're already using WhatsApp on your mobile with same mobile number. You will need another number to get this working.
