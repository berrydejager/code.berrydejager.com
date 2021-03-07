---
layout: post
title: 
date: 2014-04-11 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Getting-the-SID-of-the-current-user.png # Add image post (optional)
tags: [PowerShell, PoSh, Scripting, Windows] # add tag
---
Getting the SID of the current user

Getting the SID of user using PowerShell is remarkably simple. This one-liner retrieves the SID of the current logged on user.

```Get-WmiObject win32_useraccount -Filter "name='$env:username' and domain='$env:userdomain'"```

﻿
