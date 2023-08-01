---
title: Linux
description: A quick summary of Linux
published: true
date: 2023-08-01T21:00:31.555Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:21:30.729Z
---

# Services
[init.d](/linux-initd)
[systemctl](/linux-systemctl)
[zfs](/zfs)
[smb](/smb)

# Utilities
[bash](/bash-scripting)
[sed](/sed)
[awk](/awk)
[iconv](/iconv)
[tr](/tr)

# Commands
[Allocate a pty](/pty-alloc)
[Mounting a Windows Share](/mntwinshare)
[Mounting AWS S3 in Linux](/mnts3)
[Starting Graphical programs as root](/xheadaches)
[Preventing Interface Renaming](/linux_int_renaming)

# Setting the date
```
 date --set '2023-07-26 18:04'
```
 
 # Upgrading a callback shell
 This should probably be somewhere else, but saving
 
 
    Use bash on the attacker machine, zsh doesn’t seem to work.
    Get the nc shell.
    In the shell, execute:
```
python -c 'import pty; pty.spawn("/bin/sh")'
```
to allocate a TTY in the nc session.
    Execute
 ```
 export TERM=xterm-256color
 ```
 
 for proper color support.

 Put the shell into background using CTRL+Z.
 Configure the local shell using stty raw -echo.
 Execute fg to bring the nc shell back.
 Type reset and press enter.

Now a proper shell should be present which doesn’t close connections upon CTRL+C
(taken from https://bananamafia.dev/post/shell-upgrade/ )

There's also some simple persistence stuff using socat there.



 
