---
title: Root on IOS
description: Getting root is harder but doable
published: true
date: 2025-06-02T04:25:45.606Z
tags: 
editor: markdown
dateCreated: 2025-06-02T04:25:45.606Z
---

# Root Access

ssh in as mobile (or run terminal somehow)

```
$ ssh mobile@192.168.1.191
(mobile@192.168.1.191) Password for mobile@Ibms-iPod-touch:
Ibms-iPod-touch:~ mobile% sudo passwd root
[sudo] password for mobile:
Changing password for root.
Old Password:
New Password:
Retype New Password:
```

`su -` still doesn't work

but 
`ssh root@iphone` does
