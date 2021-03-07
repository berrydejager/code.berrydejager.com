---
layout: post
title: 
date: 2015-12-25-13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Autostart-an-application-on-Raspbian.png # Add image post (optional)
tags: [Raspberry Pi, RPi, Raspbian] # add tag
---
If you want to autostart an application in Raspbian, just edit the following file;

```~/.config/lxsession/LXDE-pi/autostart```

contents of this file

```
@lxpanel --profile LXDE-pi
@pcmanfm --desktop --profile LXDE-pi
@xscreensaver -no-splash
@hexchat
```

I added ```@hexchat``` on the bottom to have HexChat IRC client autostarted at logon.