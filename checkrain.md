---
title: Checkrain
description: A quick summary of Checkrain
published: true
date: 2023-05-23T19:05:09.544Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:17:49.513Z
---

# Checkra1n



Rufus - Make USB from iso
https://rufus.ie/en/


This is a usb iso for doing checkrain
https://github.com/SarKaa/jailm8/releases

set root=(hd0,1)
set prefix=(hd0,1)/boot/grub/
insmod normal
normal

# Success on 05/23/2023
Red USB has Ventoy and two ISOs.
Booted Ubuntu  (if UEFI gets in way boot with Grub)
Note that the usb hub with usb3.0 ports worked fine for booting.
Select the "Try Ubuntu" option
Connect to network
From terminal: 
```
apt-get-repository universe
apt update
apt install checkra1n
checkra1n
```

iPod plugged in (not through hub.  Might not matter)
was detected, hit start without altering options
Ended with USB error -77 but jailbreak was successful

The universe thing was because ncurses and some pixbuf thing were deps but couldn't be installed.  I tried installing similar packages but .deb for checkra1n wanted specific packages.  A dpkg force might have worked, but this did before I worked that out.

