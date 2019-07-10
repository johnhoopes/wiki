<!-- TITLE: Bridging -->
<!-- SUBTITLE: A quick summary of Bridging -->

# Bridging with IPRoute 2
```
#create and bring up bridge
ip link add name bridge_name type bridge
ip link set bridge_name up

#make sure eth0 is up
ip link set eth0 up

#add eth0 to bridge_name
ip link set eth0 master bridge_name

#to show existing bridges
bridge link

#to remove
ip link set eth0 nomaster

#to delete bridge entirely
ip link delete bridge_name type bridge

#Not sure what this effectively is?   Can you dhcp it?
ip addr add dev bridge_name 192.168.66.66/24

```

# Guide to intercept a port going through the bridge
http://people.apache.org/~amc/tiphares/bridge.html

So far I haven't gotten it working, but will save progress here when I do.

This worked!
https://github.com/rkok/bridge-mitm-tools

Note that the bridge-reroute requires mac addresses.  Might be able to simplify to just the firewall rules at some point.
