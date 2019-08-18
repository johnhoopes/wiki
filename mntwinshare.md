<!-- TITLE: Mounting Windows Shares -->
<!-- SUBTITLE: How to -->


```text
apt install cifs-utilities
mount -t cifs //ip.address.of.windows/location/to/mount /mnt -o user=john,password=mypassword,domain=mydomain
```
