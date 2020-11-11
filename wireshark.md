<!-- TITLE: Wireshark -->
<!-- SUBTITLE: A quick summary of Wireshark -->

# Capture Filters
Need to be in bpf style
host 1.2.3.4 and not port 3389

# Display Filters
tcp.port != 3389 (Make sure of this.... just putting a place holder here because I want it)
Using the right click to set up filter

# Decoding

# Follow TCP Stream
# USB Sniffing
[USB Sniffing](/wireshark-usbsniffing)
[USB Client in Python](/python-usbclient)

# Running wireshark with remote capture
I think there's a way to do this in the app, but there don't seem to be any videos on it.

```
ssh root@10.0.0.1 "tcpdump -U -w - 'host 10.0.0.176'" | /cygdrive/c/Program\ Files/Wireshark/Wireshark.exe -k -i -
```

