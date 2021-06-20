---
layout: post
title: Windows 11 - sneak preview
date: 2021-06-17 13:37:00 +0100
description: Windows 11 sneak preview # Add post description (optional)
img: windows-11-sneak-preview-00.png # Add image post (optional)
tags: [Windows, Windows 11, W11] # add tag
---
# "Windows 10 is the last version of windows...", ohh sure...

You might recall Satya Nadella, CEO and chairm,an of Microsoft, saying "Windows 10 is the last version of Windows". He didn't mention that it will be the final version of Windows that Microsoft will produce. The next generation of Windows is about to be revealed.

Verdict: `INSERT VERDICT`

## Brief history

Looking at the release cycle for the Windows Operation System, you will notice that the interval of the versions graduately increases. This has to do with the servicing updates and feature releases methodology that Microsoft embraces. We can only guess how long Windows 11 will last.

| Year | Release |
| --- | --- | 
| 1981 | MS-DOS |
| 1985 | Windows 1.0 |
| 1987 | Windows 2.0 |
| 1990 | Windows 3.0 |
| 1992 | Windows 3.1 |
| 1993 | Windows NT 3.1 4.0|
| 1995 | Windows 95 |
| 1998 | Windows 98 |
| 2000 | Windows Me |
| 2000 | Windows 2000 |
| 2001 | Windows XP |
| 2006 | Windows Vista |
| 2009 | Windows 7 |
| 2012 | Windows 8 |
| 2015 | Windows 10 |
| 2020 | Windows 11 | 

## Installing Windows 11

The manual installing procedure is very similar to the Windows 10 procedure, however Windows 11 sports a more modern look, shows the OS-type date modified at "30th May 2021" and the license is updated in "June 2021". It seems that this Windows 11 was already for some while in the pipeline. The Adobe Flash Player License is removed from the license.

The "limited experience" offering, which is great for experimenting with the OS, is now hidden away under "sign-in options" during the installation phase.

## UI/UX changes

The most prominent change to the user interface is the taskbar/start menu. This is now "Maccyfied" into the center of the screen.

For altering the taskbar settings you need to activate the Windows installation, see section "Windows 11 Activation" below.

The taskbar/start menu is still able to move to it's old place by setting the "Taskbar alignment" from `center` to `left`. Actually this whole taskbar menu has been changed quite a bit.

Besides the taskbar the start menu also has changed.

When the changes of the start menu can't seem to fit in your workflow you can still revert to the Windows 10 menu style. A little registry tweak does the trick for you.

`HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`

| Name | Type | Data |
| --- | --- | --- |
| Start_ShowClassicMode | REG_DWORD | 0x00000001 (1) |


## Windows 11 Activation

You can still use your KMS server to activate the Windows 11 version, while using the Windows 10 KMS keys. 



## Windows SBC/VDI optimisation


## Details of used Windows 11 .ISO file

| Name | Description |
| --- | --- | 
| Name | 21996.1.210529-1541.co_release_CLIENT_CONSUMER_x64FRE_en-us.iso |
| Size | 4874553344 bytes (4648 MiB) |
| CRC32 | 48B651E0 |
| CRC64 | 92A6B5F8D18A819D |
| SHA256 | B8426650C24A765C24083597A1EBA48D9164802BD273B678C4FEFE2A6DA60DCB |
| SHA1 | 3B6DA9194BA303AC7DBBF2E521716C809500919C |
| BLAKE2sp | 8BBEAC022C2B41EFC05EAE24AA465B6AABB61B80FBA6624CA83FD5EEA48F1A15 |
