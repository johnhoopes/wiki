<!-- TITLE: Windows -->
<!-- SUBTITLE: A quick summary of Windows -->

# WPAD - "Can you tell me where the internet is?"
[wpad](/wpad)
# CredSSP Fixing
Need to make the following key in the registry and add a value.
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters
AllowEncryptionOracle = dword32:00000002

# SMBv1 Allowance

```text
Search in the start menu for 'Turn Windows features on or off' and open it.
Search for 'SMB1.0/CIFS File Sharing Support' in the list of optional features that appears, and select the checkbox next to it.
Click OK and Windows will add the selected feature.
		
SMB 1 should be enabled by default but it won`t be used if SMB2.0 or SMB 3.0 is available.

If your NAS device only supports SMB 1.0, we could try to disable SMB 2.0 and SMB3.0 to force the Windows 10 machine to use SMB 1.0 to access the share by running the following command line.

Disable SMB2.0 and SMB 3.0
sc.exe config lanmanworkstation depend= bowser/mrxsmb10/nsi
sc.exe config mrxsmb20 start= disabled

https://support.microsoft.com/en-sg/help/2696547/detect-enable-disable-smbv1-smbv2-smbv3-in-windows-and-windows-server
```

