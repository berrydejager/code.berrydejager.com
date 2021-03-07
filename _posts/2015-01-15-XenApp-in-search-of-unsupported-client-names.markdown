---
layout: post
title: 
date: 2015-01-15 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: XenApp-in-search-of-unsupported-client-names # Add image post (optional)
tags: [PowerShell, PoSh, Scripting, Windows, Citrix, XenApp] # add tag
---
XenApp can choke on client names which contain client names which contains weird characters (according to Citrix). The result can be that the search functionality, within Citrix AppCenter, doesnt come up with any users.

![](/assets/img/XenApp-in-search-of-unsupported-client-names_img00.png)

The other manifestation of the problem can occur in the 'Servers'-node in the farm seems to hang and gives an 'Unknow error occured' error.

![](/assets/img/XenApp-in-search-of-unsupported-client-names_img01.png)

In order to gather the invalid client names please execute the following on one of the Data Zone Collectors.

```
if ( (Get-PSSnapin -Name Citrix.XenApp.Commands -ErrorAction SilentlyContinue) -eq $null )
{
Add-PSSnapin Citrix.XenApp.Commands
}

Get-XASession -farm | Where { $_.ClientName -match "[^a-zA-Z_0-9- ]"} | Get-Unique | Format-List -Property AccountName, ClientName, LogOnTime
```

This could generate the following output.

```
AccountName : berrydejager.com\berry
ClientName : Berry's MacBook
LogOnTime : 15-01-2015 10:39:13

AccountName : berrydejager.com\b.dejager
ClientName : PC_BÉRRY
LogOnTime : 15-01-2015 8:24:34

AccountName : berrydejager.com\berry.dejager
ClientName : PC(1337)
LogOnTime : 15-01-2015 13:59:15

AccountName : berrydejager.com\Berry.de.Jager
ClientName : ♠ICA Client
LogOnTime : 15-01-2015 16:02:39
```

So when the invalid hostnames are found please rename them. In this example you will notice the following unsupported characters;

```
'
É
( )
♠
```


Please read the Microsoft's 'KB909264 - Naming conventions in Active Directory for computers, domains, sites, and OUs' support article as a guide.

As usually it's always a good practice to upgrade the Citrix Receiver to the latest version.