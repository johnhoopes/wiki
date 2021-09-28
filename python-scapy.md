<!-- TITLE: Python Scapy -->
<!-- SUBTITLE: A quick summary of Python Scapy -->

# Sniffing for packets

```text
from scapy.all import *
a = sniff(filter = "host 10.0.0.1", iface = "eth1", count = 1)
a.nsummary()

```
