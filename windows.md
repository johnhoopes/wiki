<!-- TITLE: Windows -->
<!-- SUBTITLE: A quick summary of Windows -->

# CredSSP Fixing
Need to make the following key in the registry and add a value.
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters
AllowEncryptionOracle = dword32:00000002