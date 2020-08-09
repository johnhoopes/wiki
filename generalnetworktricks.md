<!-- TITLE: General Network Tricks -->
<!-- SUBTITLE: A quick summary of Generalnetworktricks -->

# Proxychains

/etc/proxychains4.conf
```
[ProxyList]
socks5 localhost 12345
```

$proxychains bash
$anything in that bash session is proxied
