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
```

