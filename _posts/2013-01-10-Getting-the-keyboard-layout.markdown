---
layout: post
title: 
date: 2013-01-10 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Getting-the-keyboard-layout.png # Add image post (optional)
tags: [PowerShell, PoSh, Scripting, Windows] # add tag
---
	[string]$HiveKey = “HKCU:\Keyboard Layout\Preload”
	$Values=(Get-Item $HiveKey).GetValueNames() | Sort -Descending
	ForEach ($Value in $Values)
	{
	Write-Host SetLocale (Get-ItemProperty $HiveKey).($value)
	}

