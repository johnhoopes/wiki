<!-- TITLE: Linux Interface Renaming -->
<!-- SUBTITLE: Preventing Linux from renaming interfaces -->

# Preventing Linux from renaming interfaces
in /etc/default/grub

```text
#HOOPES Note the net.ifnames=0 and biosdevname=0 are to prevent renaming interfaces
GRUB_CMDLINE_LINUX_DEFAULT="quiet modprobe.blacklist=intel_powerclamp splash net.ifnames=0 biosdevname=0"
```

