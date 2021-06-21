---
layout: post
title: Windows 11 - sneak preview
date: 2021-06-17 13:37:00 +0100
description: Windows 11 sneak preview # Add post description (optional)
img: Window_11_sneak_preview.png # Add image post (optional)
tags: [Windows, Windows 11, W11] # add tag
---
# "Windows 10 is the last version of windows...", ohh sure...

You might recall Satya Nadella, CEO and chairm,an of Microsoft, saying "Windows 10 is the last version of Windows". He didn't mention that it will be the final version of Windows that Microsoft will produce. The next generation of Windows is about to be revealed at the [#MicrosoftEvent](https://www.microsoft.com/en-us/windows/event) on the 24th of June 2021 at 11:00  Eastern Time. Click [here](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWFdr0) for the reminder.

The verdict: As far as i can see it's a little more than just dressing up the Windows 10 interface visually. The interface of the operation system needs to compete with itself and other OS's to stay relevant in a designers world and at the same time it needs to be enticing for the end-user.

## Brief history

Looking at the release cycle for the Windows Operation System, you will notice that the interval of the versions graduately increases. This has to do with the servicing updates and feature releases methodology that Microsoft embraces. We can only guess how long Windows 11 will last.

 The support lifecycle date of Windows 10 listed a 10-year support lifecycle.

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

### Windows 11 Activation

You can still use your KMS server to activate the Windows 11 version, while using the Windows 10 KMS keys.

### Intune / Autopilot

Deploying using Intune / Autopilot also worked. Having that said; Windows 11 reported itself with an OS version `10.0.21996.1`. Is it that the Windows 10 has been skinned or the version number need to be updated, who knows?

## UI/UX changes

The version tested showed "Version Dev (OS Build 21996.1)". 

### Overal re-design

A brand new logo, by unskewing the Windows 10 logo to a square format, gets my eyes a little watery; Is this the real life? Is this just fantasy? It certainly looks more contemporary and elegant to me.

Shiny news icons, rounded corners, thin sliders and new animations are part of the design overhaul.

The OOBE also sports a new look. Not that is that important in a VDI world, `unattended.xml` and Autopilot are our friends. Most likely the ADK and unattend.xml will not change that much.
### Taskbar / Start menu

The most prominent change to the user interface is the taskbar/start menu. This is now "Maccyfied" into the center of the screen.

For altering the taskbar settings you need to activate the Windows installation, see section "Windows 11 Activation" below.

The taskbar/start menu is still able to move to it's old place by setting the "Taskbar alignment" from `center` to `left`. Actually this whole taskbar menu has been changed quite a bit.

Besides the taskbar the start menu also has changed.

When the changes of the start menu can't seem to fit in your workflow you can still revert to the Windows 10 menu style. A little registry tweak does the trick for you.

`HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`

| Name | Type | Data |
| --- | --- | --- |
| Start_ShowClassicMode | REG_DWORD | 0x00000001 (1) |

As this setting resides in the current user context of the Explorer UI, you need to log off and logon again to see the changes. Restarting the `explorer.exe` will also do the trick.

## Windows SBC/VDI optimisation

### VMware OSOT

The [VMware OS Optimization Tool](https://flings.vmware.com/vmware-os-optimization-tool) helps in preparing and optimizing Windows 10 and Windows Server 2019, 2016 systems for use with VMware Horizon. For Windows 7, 8.1, and Server 2012, 2012 R2, an older version (b1130) of the OS Optimization Tool is available for download.

### Summary

At a high level, the process of creating a golden image VM consists of the following steps. A a step by step walk-through of the complete process, is given in the [Creating an Optimized Windows Image for a VMware Horizon Virtual Desktop](https://techzone.vmware.com/creating-optimized-windows-image-vmware-horizon-virtual-desktop) guide.

*   [Optimize](https://techzone.vmware.com/resource/vmware-operating-system-optimization-tool-guide#optimize) – Analyze, select optimizations, and apply them to the Windows image.
    *   Analyze - compares the settings of the template against the machine settings.
    *    Common Options - quickly and easily choose and set preferences to control common functionality.
    *   Optimize - applies the chosen selections.
*   [Generalize](https://techzone.vmware.com/resource/vmware-operating-system-optimization-tool-guide#generalize) - helps in running the system preparation tool (Sysprep) by generating a customizable and editable unattend answer file.
*   [Finalize](https://techzone.vmware.com/resource/vmware-operating-system-optimization-tool-guide#finalize) - automate and help with some of the common clean up tasks that are typically run just before using the prepared image.
*   [Update](https://techzone.vmware.com/resource/vmware-operating-system-optimization-tool-guide#update) - re-enable Windows Update functionality on an image that has previously been optimized and had this disabled.

For more information on how to use the OS Optimization Tool see the [VMware Operating System Optimization Tool Guide](https://techzone.vmware.com/resource/vmware-operating-system-optimization-tool-guide#introduction
).

### Applying OSOT

Version used: [VMware OSOT, version B2003 - 20th April 2021](https://techzone.vmware.com/resource/vmware-operating-system-optimization-tool-guide#update) 

For applying OSOT to Windows 11 we need a specific Windows 11 template, which isn't available now/yet. Therefor we just select the current 'Windows 10 and Server 2016 or later (v1.8)' template, published by VMware, available from the interface.


### Citrix Optimizer

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
