<!-- TITLE: Tor -->
<!-- SUBTITLE: A quick summary of Tor -->

# Setting up Vanity Onion Addresses

# SSHing to TOR Servers
```
ssh -o VerifyHostKeyDNS=no -o User=user -o CheckHostIP=no\
    -o IdentitiesOnly=yes \
    -o ProxyCommand="nc -X 5 -x localhost:9050 %h %p" \
    -i ~/.ssh/sshhs1.rsa domain
```


Probably want to do this
```
echo "UseDNS no" >> /etc/ssh/sshd_config
```

# How Onion V3 works
https://matt.traudt.xyz/p/FgbdRTFr.html
