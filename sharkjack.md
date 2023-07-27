---
title: SharkJack
description: Tips and tricks for sharkjack
published: true
date: 2023-07-27T01:44:31.672Z
tags: 
editor: markdown
dateCreated: 2023-07-27T01:44:31.672Z
---

# NETMODE
DHCP
```
NETMODE DHCP_CLIENT
```

# SSH
Should be enabled in arming mode.  Not sure what default password is.  Mine is set to usual.

# Date
SSL won't work till date is set.
```
 date --set '2023-07-26 18:04'
 ```
 
 # HELP
 HELP at cmdline to get basics
 
 # UPDATE_PAYLOADS
 If date is set this should update payloads
 
 # LIST
 List out the payloads.  Currently:
 
 ```
 Payloads
========

example
---------
    cloudc2-multi-file-exfiltration

execution
---------
    SharkDOS

exfiltration
---------
    ms-teams-exfiltration

recon
---------
    Network-Recon-With-Email-Exfil
    Network-Recon-framework-payload-with-logging-notification-and-exfiltration
BusyBox v1.28.4 () multi-call binary.

Usage: basename FILE [SUFFIX]

Strip directory path and .SUFFIX from FILE

    Nmap-C2
    Nmap-With-Pastebin-Exfil
    SLAP-Nmap-to-Slack
    Sample-Nmap-Payload
    Telegram-Nmap-to-Telegram
    ipinfo
    netdiscover
    simple-tcpdump

remote_access
---------
    On-Site

util
---------
    Backup-and-Restore-scripts-with-logging-and-notification
    Jack-Tester
    internet-access-tester
    mac-changer
    package-installer
    ping-tester
    ssh-ip-blinker

```

 Changed distfeeds to make it actually work:
 
 ```
 src/gz openwrt_core http://downloads.openwrt.org/releases/18.06.0/targets/ramips/mt76x8/packages
src/gz openwrt_base http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/base
src/gz openwrt_luci http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/luci
src/gz openwrt_packages http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/packages
src/gz openwrt_routing http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/routing
src/gz openwrt_telephony http://downloads.openwrt.org/releases/18.06.0/packages/mipsel_24kc/telephony
 ```
 