---
title: Mobile Adb
description: A quick summary of Mobile Adb
published: true
date: 2023-02-24T17:16:50.439Z
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

# Setting and Deleting global Proxy
Setting
```
adb shell settings put global http_proxy <ip:port>
```

Deleting
```
adb shell put global http_proxy :0
```