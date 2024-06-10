---
title: My Wireless Adapters
description: Enumerating various adapters that I have
published: true
date: 2024-06-10T03:59:23.302Z
tags: 
editor: markdown
dateCreated: 2024-06-10T03:35:48.660Z
---

# Alfa Adapters

(actually have two of these.  Don't need to carry both)

Color:  Blue-Green
Desc: 802.11 b/g/n Long Range 
Mac: 00:c0:ca:47:a9:2b

        Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * AP/VLAN
                 * monitor
                 * mesh point

```
root@dragon-VirtualBox:~# aireplay-ng -9 wlan0mon                                                                                                   
21:42:35  Trying broadcast probe requests...                                                                                                        
21:42:35  Injection is working!                                                                                                                     
21:42:37  Found 15 APs                                                                                                                              
```

---

# Wedge

Color: Black
Desc: Direct USB.  Looks like a wedge, dual antenna
MAC: Dragon doesn't have the driver for it. virtbox controller might also be issue
USB Desc:  MediaTek Inc. MT7612U 802.11a/b/g/n/ac Wireless Adapter

Probably an important card.  Will have to come back to it.
Check straight ubuntu


# Panda
Color: Black
Desc:  Says Panda Wireless on top.  Has RFKill button I think.
USB Desc: Ralink Technology, Corp. RT5572 Wireless Adapter
MAC: 9c:ef:d5:fd:1f:08

Can do bgn channels and 'a' channels


```
        Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * AP/VLAN
                 * monitor
                 * mesh point
```
Need to test 5G AP capability

```
root@dragon-VirtualBox:~# aireplay-ng -9 wlan0mon
21:58:39  Trying broadcast probe requests...
21:58:39  Injection is working!
21:58:41  Found 16 APs
```
