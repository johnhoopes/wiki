---
title: Mobile Adb
description: A quick summary of Mobile Adb
published: true
date: 2023-01-18T21:58:09.440Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:22:38.237Z
---

# PS Listing in ADB
```
ps -A
```

# ADB over Network

Using USB (not sure if this could be done via shell
```
adb tcpip 5555
```

Over network
```
adb connect ip:port
```
