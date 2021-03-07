---
layout: post
title: 
date: 2014-10-31 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Simplistic-way-of-getting-memory-statistics.png # Add image post (optional)
tags: [PowerShell, PoSh, Scriptint, Windows] # add tag
---



    # $Author: berrydejager $
    # $Rev: 1.0 $
    #
    # Version control:
    #
    # 1.0 Initial version

    #
    # Functions definitions
    #

    Function GetFreeMem
    {
    Param([string]$ComputerName)
    Write-host “————————————————————————————”
    Write-host “- START SCANNING $Computername —————————————————”
    Write-host “————————————————————————————”
    Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles
    Write-host “————————————————————————————”
    Write-host “- END SCANNING $Computername —————————————————–”
    Write-host “————————————————————————————”
    Write-Host ” ”
    Write-Host ” ”
    }
    ###
    ### Start of Main Routine
    ###

    clearGetFreeMem SERVER001
    GetFreeMem SERVER002
    GetFreeMem SERVER003

    ###
    ### End of Main Routine
    ###

