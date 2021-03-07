---
layout: post
title: 
date: 2016-10-07 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Installing-OMSA-in-VMware-ESXi.png # Add image post (optional)
tags: [Dell, Linux, OMSA, Perc, PowerCLI, Scripting, VMware, vSphere] # add tag
---

#### Download the OMSA 8.3 package

Navigate to [Dell OpenManageServer Administrator vSphere Installation Bundle (VIB) for ESXi 6.0, v8.3](http://downloads.dell.com/FOLDER03572457M/1/OM-SrvAdmin-Dell-Web-8.3.0-1908.VIB-ESX60i_A00.zip) to retrieve the OMSA package.


#### Prepare the ESXi server for temporary SSH traffic

Setup your ESXi server for SSH connections by starting the ```TSM-SSH``` service from the services list.

Host -> Manage -> Services -> TSM-SSH -> right-click and ```Start```

#### Installing the OMSA 8.3 package

Now use (Win)SCP copy the downloaded file to ```/tmp``` of your ESXi server.

Log into to the ESXi server using SSH to execute:

```esxcli software vib install -d=/tmp/OM-SrvAdmin-Dell-Web-8.3.0-1908.VIB-ESX60i_A00.zip```

    Installation Result
    Message: The update completed successfully, but the system needs to be rebooted for the changes to be effective.
    Reboot Required: true
    VIBs Installed: Dell_bootbank_OpenManage_8.3.0.ESXi600-0000
    VIBs Removed:
    VIBs Skipped:

Reboot

Log into to the ESXi server using SSH to execute:

```esxcli software vib list | grep -i dell```

    Name Version Vendor Acceptance Level Install Date
    —————————– ———————————— —— —————- ————
    OpenManage 8.3.0.ESXi600-0000 Dell PartnerSupported 2016-10-07

http://servername:1311