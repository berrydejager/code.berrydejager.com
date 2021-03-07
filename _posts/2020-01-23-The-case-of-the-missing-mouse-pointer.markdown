---
layout: post
title: 
date: 2020-01-23 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: The-case-of-the-missing-mouse-pointer.png # Add image post (optional)
tags: [Microsoft, Windows, RDP] # add tag
---
Suddenly, while working with multiple RDP sessions from my W10 VDI machine, the ‘normal select’ mouse pointer vanished. Remarkably the other cursors, like ‘text select’ and ‘link select’ ,would still show.

Very frustrating as the root of the problem remains unknow to me. While trying to resolve this i came up with a very easy fix.

Within the RDP execute the following sequence:

*	Start ‘main.cpl’
*	Navigate to ‘Pointers’ tab using the Tab-key
*	Press ALT+e to unthick the ‘Enable Pointer Shadow’ option
*	Press ALT+a to apply the settings

![2020-01-23-The-case-of-the-missing-mouse-pointer.png](/assets/img/2020-01-23-The-case-of-the-missing-mouse-pointer_img00.png)

The mouse pointer has returned again.

Faith in Windows; restored... for now...

