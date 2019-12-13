<!-- TITLE: Virtualbox -->
<!-- SUBTITLE: A quick summary of Virtualbox -->

# Vboxmanage
```
vboxmanage list vms
vboxmanage list runningvms
vboxmanage showvminfo <uuid|vmname>
vboxmanage startvm <uuid|vmname> --type headless
vboxmanage controlvm vm <uuid|vmname> poweroff

vboxmanage guestcontrol run --exe -- <program/arg0> arg1...
vboxmanage guestcontrol copyfrom / copyto

vboxmanage snapshot <uuid|vmname> take|list|restore|

vboxmanage debugvm <uuid|vmname> dumpvmcore
vboxmanage debugvm <uuid|vmname> info
vboxmanage debugvm <uuid|vmname> getregisters
vboxmanage debugvm <uuid|vmname> setregisters
```

