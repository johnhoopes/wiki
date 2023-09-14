---
title: IPv6 - Notes
description: Quick thing about IPv6 that I've collected
published: true
date: 2023-09-14T04:46:02.396Z
tags: 
editor: markdown
dateCreated: 2023-09-14T01:44:38.504Z
---

Source of some of this content: https://blogs.infoblox.com/ipv6-coe/fe80-1-is-a-perfectly-valid-ipv6-default-gateway-address/

# Addr Spaces

2000::/3 - Global Unicast Addrs (routable IPs)
FD00::/8 - Unique Local Addresses  (like 10. but you're not actually supposed to use)
FE80::/10 - When a host boots up, it automatically assigns this space to interface
FE80:0000:0000:0000:abcd:abcd:abcd:abcd - the final 64-bits provide the unique Interface Identifier.
FF02:: - Link Local Multicast (like broadcast)


# Discovery of Gateway
Link-local IPv6 addresses are on every interface of every IPv6-enabled host and router.  They are essential for LAN-based Neighbor Discovery communication.  After the host has gone through the Duplicate Address Detection (DAD) process ensuring that its link-local address (and associated IID) is unique on the LAN segment, it then proceeds to sending an ICMPv6 Router Solicitation (RS) message sourced from that address.

When the router receives the host’s Router Solicitation (RS) message (sent in the attempt to find any router available on the link and to reach the rest of the network), the router immediately replies with an ICMPv6 Router Advertisement (RA) message.  That RA message is also sourced from the router’s own link-local address.  When the host receives the RA message, it reads the contents, follows the address configuration method indicated in the packet, and, in the case where SLAAC is the address configuration method, uses the RA-included IPv6 /64 prefix to configure a globally-scoped address.  The host will then use the router’s link-local address (and MAC contained in the RA) as its default gateway.

# Adding IPv6 Addrs
Using "ip" 
```# /sbin/ip -6 addr add <ipv6address>/<prefixlength> dev <interface> ...```

Using "ifconfig" 
```# /sbin/ifconfig <interface> inet6 add <ipv6address>/<prefixlength>```


    