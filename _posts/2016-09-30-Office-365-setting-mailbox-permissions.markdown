---
layout: post
title: 
date: 2016-09-30 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Office-365-setting-mailbox-permissions.png # Add image post (optional)
tags: [Microsoft, Office 365, PowerShell] # add tag
---
While looking for a method to migrate Office 365 mail i have notices that quite a few blogs copy/paste information without actually testing the procedure.

```
$AdminUser = berrydejager
$UserCredential = Get-Credential
$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $Session

$MBXS = Get-Recipient -RecipientType UserMailbox

ForEach ($MBX in $MBXS)
{
Write-Host $MBX.name
Add-MailboxPermission $MBX.name -User $AdminUser -AccessRights FullAccess -InheritanceType All

Write-Host $MBX.name
$PSTFile = "C:\_PST\Mailbox_$MBX.name.pst" ## add Your new PST file name path
Write-Host $PSTFile
$outlook = New-Object -ComObject outlook.application
$namespace = $Outlook.GetNameSpace("MAPI")
$NameSpace.AddStore($PSTFile) ## Add the new PST to the Current profile
$NEWStore = $namespace.Stores | ? {$_.filepath -eq $PSTFile} ## Get the New Store
}
```