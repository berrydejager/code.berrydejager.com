---
layout: post
title: 
date: 2013-06-14 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Getting-the-printer-details.png # Add image post (optional)
tags: [PowerShell, PoSh, Scripting, Windows] # add tag
---
```


Function GetVersion{

	Param ([string]$PrintServer = “localhost”)
	$Results = @()

	ForEach ($Driver in (Get-WmiObject Win32_PrinterDriver -ComputerName $PrintServer))
	{ 	$Drive = $Driver.DriverPath.Substring(0,1)
		$Results += New-Object PSObject -Property @{
			Name = $Driver.Name
			Server = $Driver.PSComputername
		}
		Write-Host $Results
	}
	
	$Results

	}
cls

Add-PSSnapin Citrix* -ErrorAction SilentlyContinue

$GetXAZone = Get-XAZone
$XAZoneName = $GetXAZone.ZoneName
$XAServerList = Get-XAServer -ZoneName $XAZoneName -OnlineOnly
$CompleteList = Foreach ($item in $XAServerList.servername){GetVersion $item
#add-content -path GetPrinterDetails_log.txt -value “Citrix Server: $item”
}
$SortedList = $CompleteList | Sort-Object -Property name -Unique

Foreach ($item in $SortedList.name){write-host $Item}
$SortedListCount = $SortedList.Count
$XAServerListCount = $XAServerList.Count
# add-content -path GetPrinterDetails_log.txt -value “$SortedListCount unique drivers on $XAServerListCount Citrix servers”

# GetVersion SDCACTXDSKD2 | Sort-Object -Property name -Unique

```