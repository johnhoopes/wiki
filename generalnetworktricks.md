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

# Funky addressing
May be able to use this on AWS/GCP/Azure tests
```
::ffff:127.0.0.1
```
