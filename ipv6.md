---
title: IPv6 - Notes
description: Quick thing about IPv6 that I've collected
published: true
date: 2023-09-14T02:03:39.641Z
tags: 
editor: markdown
dateCreated: 2023-09-14T01:44:38.504Z
---

# Addr Spaces

2000::/3 - Global Unicast Addrs (routable IPs)
FD00::/8 - Unique Local Addresses  (like 10. but you're not actually supposed to use)
FE80::/10 - When a host boots up, it automatically assigns this space to interface
FE80:0000:0000:0000:abcd:abcd:abcd:abcd - the final 64-bits provide the unique Interface Identifier.
FF02:: - Link Local Multicast (like broadcast)
