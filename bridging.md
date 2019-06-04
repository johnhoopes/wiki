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
