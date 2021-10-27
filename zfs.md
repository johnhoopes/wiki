<!-- TITLE: Zfs -->
<!-- SUBTITLE: A quick summary of Zfs -->

# Mounting vault

Note that the disks have to be in dmesg.  

`zpool import
zpool import vault-pool
zfs mount
`

Not sure if mount at end needed to be done or if it was already mounted, but it was there after I did it.
