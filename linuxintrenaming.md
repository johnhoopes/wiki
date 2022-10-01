<!-- TITLE: Linuxintrenaming -->
<!-- SUBTITLE: A quick summary of Linuxintrenaming -->

# Preventing Linux from renaming interfaces
in /etc/default/grub
`#HOOPES Note the net.ifnames=0 and biosdevname=0 are to prevent renaming interfaces
GRUB_CMDLINE_LINUX_DEFAULT="quiet modprobe.blacklist=intel_powerclamp splash net.ifnames=0 biosdevname=0"`
