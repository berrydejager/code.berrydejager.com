---
layout: post
title: 
date: 2014-04-10 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Screen-flickers-on-IGEL-Thin-Client- while-using-XenApp-6.x-(EnableOSS).png # Add image post (optional)
tags: [PowerShell, PoSh, Scripting, Windows] # add tag
---
When you experience flickering of certain (in our case on blueish) parts of an internet website which being connected to a XenApp 6.x farm using a IGEL Thin Client you might need to read these Citrix articles :

[CTX133935 - Flickering or Other Display Issues Might be Seen when Adaptive Display or Progressive Display is Enabled](http://support.citrix.com/article/CTX133935)


and

[CTX128332 - Images are Tinted Blue in Published Photoshop](http://support.citrix.com/article/CTX128332)


This can easily be eliminated by setting the following setting in the setup of the Linux thin client:

```
IGEL Setup -> System -> Registry -> ICA -> wfclient -> enableoss -> ◘ Enable off-screen drawing.
```

Unthicking this setting eliminates the problematic progressive / adaptive display feature when using OSS (Off-Screen Surfaces).

![](/assets/img/Screen-flickers-on-IGEL-Thin-Client- while-using-XenApp-6.x-(EnableOSS)_img00.png)
