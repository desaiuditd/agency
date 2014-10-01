---
layout: post
status: publish
published: true
title: Skype Audio on Ubuntu
author:
  display_name: Udit Desai
  login: desaiuditd
  email: desaiuditd@gmail.com
  url: http://about.me/desaiuditd
author_login: desaiuditd
author_email: desaiuditd@gmail.com
author_url: http://about.me/desaiuditd
wordpress_id: 69
wordpress_url: http://blog.incognitech.in/?p=69
date: '2014-01-05 21:24:46 -0500'
date_gmt: '2014-01-05 15:39:46 -0500'
categories:
- Tech
tags:
- Ubuntu
- skype
- audio
- voice calls
comments: []
---

Here comes another experimental solution for the Skype Audio problem in Linux Distros. You must have noticed that your Skype does not trigger the typical Sign-in sound when you log in to your Skype account at your machine start-up. It also must have happened that you are not able to execute your voice calls over Skype. So all your music files, video files, music players, video players are working except Skype audio on Ubuntu machine of yours is dead. Here is a trick that you can follow to solve this little problem.

1. Select Skype Options.
2. Go to "Sound Devices" section.
3. Now here comes the tricky part. You will have to set microphone device, speaker device and ringing device that you want your Skype application to use. By default Skype tries to use the default dedicated device for its task; but due to incompatible driver issue or due to any unknown reason it doesn't go well with the default device.
4. If your motherboard is of Intel family then here's the trick. Select the options as given in the screenshots provided below.

    - **Microphone :** HDA Intel PCH, STAC92xx Analog (hw:1,0)<br />
    - **Speakers :** HDA Intel PCH, STAC92xx Analog hardware device without any software conversions (plughw: CARD = PCH, DEV = 0)
    - **Ringing :** HDA Intel PCH, STAC92xx Analog hardware device without any software conversions (plughw: CARD = PCH, DEV = 0) Normally, you can keep same device for Ringing & Speakers.

5. Many community people have opinion that you will have to play around with the possible choices over here and try out each combination with a little guess work.
6. But my guess is try to go with the device which has name of your motherboard family variant. So e.g., if your mother board is of Intel family then try out combinations with Intel devices. These are some of the other combinations that I found on community forums which might work.

    - Sound In: HDA Intel (hw:Intel, 0)
    - Sound Out: HDA Intel (plughw:Intel, 0)
    - Ringing: HDA Intel (plughw, Intel, 0)

7. After selecting a proper combination of devices; test your configuration with "Make a test sound" & "Make a test call" buttons. You will be able to hear the log in sound and make a successful test call.

**Screenshots:**

![](/uploads/2014/01/Screenshot-from-2014-01-05-202902.png)
![](/uploads/2014/01/Screenshot-from-2014-01-05-203626.png)
![](/uploads/2014/01/Screenshot-from-2014-01-05-205736.png)
