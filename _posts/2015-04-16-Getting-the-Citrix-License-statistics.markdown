---
layout: post
title: 
date: 2015-04-16 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Getting-the-Citrix-License-statistics.png # Add image post (optional)
tags: [PowerShell, PoSh, Scripting, Windows,. Citrix, Citrix License server] # add tag
---

```
[string]$result = (Get-Content 'c:\temp\CTX\CTX_licenses.txt')[4 .. 4]
[string]$result_date = Get-Date
$result_inuse = $result.substring(11,6)
$result_users = $result.substring(31,6)
$result_devices = $result.substring(47,6)
$result_string = $result_date+";"+$result_inuse+";"+$result_users+";"+$result_devices
Add-Content -path 'c:\temp\CTX\CTX_licenses.txt' -Value $result_string
```