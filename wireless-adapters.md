---
title: My Wireless Adapters
description: Enumerating various adapters that I have
published: true
date: 2024-06-10T06:12:03.189Z
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
MAC: 8c:88:2a:00:7e:3c
USB Desc:  MediaTek Inc. MT7612U 802.11a/b/g/n/ac Wireless Adapter

Probably an important card.  Will have to come back to it.
Check straight ubuntu

Throwing dmesg messages.  Works, but probably bad idea.  Not bad load.

[ 6694.441160] xhci_hcd 0000:00:0c.0: ERROR Transfer event TRB DMA ptr not part of current TD ep_index 8 comp_code 13
[ 6694.441161] xhci_hcd 0000:00:0c.0: Looking for event-dma 0000000001113d20 trb-start 0000000001113d30 trb-end 0000000001113d60 seg-start 0000000001113000 seg-end 0000000001113ff0

```
        Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * AP/VLAN
                 * monitor
                 * mesh point
                 * P2P-client
                 * P2P-GO
```

```
root@dragon-VirtualBox:~# iwconfig wlan0mon channel 44
root@dragon-VirtualBox:~# aireplay-ng -9 wlan0mon
00:05:38  Trying broadcast probe requests...
00:05:38  Injection is working!                    
00:05:40  Found 4 APs                                                          
```



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

# ANEWKODI
Color: Black
Desc: small adapter
USB Desc: 802.11ac WLAN Adapter
MAC: 00:e0:4c:0a:79:23
Doesn't show up in Dragon with iwconfig (had to add driver. Info below)


The 8821au driver seems to have special settings for hostapd in 2.4 and 5 ghz.
They'll live in /etc/modprobe.d/8821au.conf 
May need reboot, may just be able to reload one or more modules.

GIT for the driver:
https://github.com/morrownr/8821au-20210708
apt install gcc-12
./install_driver.sh

```
        Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * monitor
                 * P2P-client
                 * P2P-GO

```

```
root@dragon-VirtualBox:~/8821au-20210708# aireplay-ng -9 wlx00e04c0a7923
23:39:02  Trying broadcast probe requests...
23:39:02  Injection is working!
23:39:04  Found 6 APs
```