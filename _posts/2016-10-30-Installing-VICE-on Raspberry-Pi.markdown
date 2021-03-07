---
layout: post
title: 
date: 2016-10-30 13:37:00 +0100
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Installing-VICE-on Raspberry-Pi.png # Add image post (optional)
tags: [Raspberry-Pi, VICE, Raspbian, Commodore 64, C64] # add tag
---
Prior to installing VICE on your Jessie distribution of Raspbian you need to alter the sources list.

```sudo nano /etc/apt/sources.list```

#### Add the following lines on the end of the file

```deb http://ftp.nl.debian.org/debian/ jessie main contrib```

Execute the following commands to completely install VICE including the ROM files.

#### Run the source update

```apt-get update```

#### Install VICE from the newly added source

```apt-get install vice```

#### Fetch, unpack and copy ROM files

```
cd ~
wget http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/old/vice-1.5-roms.tar.gz
tar -xvzf vice-1.5-roms.tar.gz
sudo cp -a vice-1.5-roms/data/* /usr/lib/vice/
```

#### Start VICE
```x64```
