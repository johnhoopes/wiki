---
title: Checkrain
description: A quick summary of Checkrain
published: true
date: 2025-04-30T18:10:07.059Z
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
echo 'deb https://assets.checkra.in/debian /' >> /etc/apt/sources.list
apt-key adv --fetch-keys https://assets.checkra.in/debian/archive.key
apt-add-repository universe
#note that the universe command above caused issues with cdrom repo.  Can kill it
apt update
apt install checkra1n
checkra1n
```

iPod plugged in (not through hub.  Might not matter)
was detected, hit start without altering options
Ended with USB error -77 but jailbreak was successful

The universe thing was because ncurses and some pixbuf thing were deps but couldn't be installed.  I tried installing similar packages but .deb for checkra1n wanted specific packages.  A dpkg force might have worked, but this did before I worked that out.

# Success on 09/17/2024
Updated to 15.8.3 - Checkra1n doesn't work anymore
Now must use palera1n

Still using ubuntu Live 22.04
```
Hitting enter with usb drive plugged might get to setup on thinkpad
connect to wireless
apt install tmux net-tools curl
put thinkpad back in secure when done.
```

These instructions:
https://ios.cfw.guide/installing-palera1n/#running-palera1n
```
    Open up a terminal window
    Run sudo systemctl stop usbmuxd
    Run sudo usbmuxd -f -p
    Open up another terminal window
    Run sudo /bin/sh -c "$(curl -fsSL https://static.palera.in/scripts/install.sh)"
    #/usr/local/bin/palera1n -f   (-f didn't work on 10/2/2024 - -l should still work, if root needed ssh and sudo it.)
    /usr/local/bin/palera1n -l
```
Note 1 - The instructions in app for dfu mode are wrong.  Instead of using home button use volume down and power.

Note 2 - It timed out waiting for download mode.  Unplug and replug cable and it went into download mode.
Timed out again.  Reran exploit, time out, unplug/replug, and download mode seemed to proceed ok.  Booted kernel, and palera1n was installed.  

# Success on 04/30/2025
Followed above, but key that I forgot to do sudo on palera1n and wasn't root.  It would just sit there trying to detect devices and never find the device that was in recovery mode.

