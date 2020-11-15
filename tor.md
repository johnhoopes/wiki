<!-- TITLE: Tor -->
<!-- SUBTITLE: A quick summary of Tor -->

# Setting up Vanity Onion Addresses
Mostly from https://opensource.com/article/19/8/how-create-vanity-tor-onion-address
## V2
```
$ git clone https://github.com/ReclaimYourPrivacy/eschalot.git
$ cd eschalot-1.2.0
$ make

$ ./eschalot -t 24 -r '^vanity' >> vanityonion.txt
```
## V3
```
$ git clone https://github.com/cathugger/mkp224o.git
$ cd mkp224o
$ ./autogen.sh
$ ./configure
$ make

$ ./mkp224o filterword fast -t 24 -v -n 4 -d ./dirtoputthem/

```

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
Note that V3 requires servers to have public keys for clients.  Good for internal happenings, not for public addr.

