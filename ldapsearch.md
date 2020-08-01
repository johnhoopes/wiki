<!-- TITLE: Ldapsearch -->
<!-- SUBTITLE: A quick summary of Ldapsearch -->

At least one instances where search showed lm password hashes
# How to call
```
verify null bind works:
ldapsearch -h <ip> -p 389 -x -s base -b '' "(objectClass=*)" "*"

I think net in following is part of fqdn... verify.
ldapsearch -h <ip> -p 389 -x -b "dc=domainname,dc=net" > ldapsearch.users
```

