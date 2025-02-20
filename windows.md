---
title: Windows
description: A quick summary of Windows
published: true
date: 2025-02-15T20:20:16.152Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:29:03.176Z
---

# Active Directory Attacks
[mimikatz](/mimikatz) - Need SYSTEM access on a Domain joined machine
[golden-ticket](/goldenticket) - Need kerberos hash from DC, and Domain Sid (which should be easy)

[windows-attack-articles](/windows-attack-articles) - to read someday

# Speak to me in English please
Changes windows error messages back to english

```
C:\> chcp 437
```


# WPAD - "Can you tell me where the internet is?"
[wpad](/wpad)

# Current patch checking
https://docs.microsoft.com/en-us/windows/security/threat-protection/mbsa-removal-and-guidance

# CredSSP Fixing also NLA (In case that's searched for)
## On Clients that cant connect
Need to make the following key in the registry and add a value.
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters
AllowEncryptionOracle = dword32:00000002

```text
reg version
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters" /v AllowEncryptionOracle /d 2 /f
```

## On Servers that wont let you connect
```text
reg add "HKLM\System\CurrentControlSet\Control\Terminal Server\Winstations\RDP-Tcp" /v UserAuthentication /t REG_DWORD /d 0 /f
```

## Using Crackmapexec
```text
 crackmapexec smb 10.0.0.186 -u Administrator -p NewAdminPassword1! --exec-method smbexec -x 'reg add "HKLM\System\CurrentControlSet\Control\Terminal Server\Winstations\RDP-Tcp" /v UserAuthentication /t REG_DWORD /d 0 /f'
 ```
 
Hasn't worked yet:
```text
crackmapexec smb 10.0.0.186 -u Administrator -p NewAdminPassword1! --exec-method smbexec -X 'Disable-WSManCredSSP -Role Server'
```

# SMBv1 Allowance

```text
Search in the start menu for 'Turn Windows features on or off' and open it.
Search for 'SMB1.0/CIFS File Sharing Support' in the list of optional features that appears, and select the checkbox next to it.
Click OK and Windows will add the selected feature.
```

SMB 1 should be enabled by default but it won`t be used if SMB2.0 or SMB 3.0 is available.

If your NAS device only supports SMB 1.0, we could try to disable SMB 2.0 and SMB3.0 to force the Windows 10 machine to use SMB 1.0 to access the share by running the following command line.

Disable SMB2.0 and SMB 3.0
```text
sc.exe config lanmanworkstation depend= bowser/mrxsmb10/nsi
sc.exe config mrxsmb20 start= disabled
```

https://support.microsoft.com/en-sg/help/2696547/detect-enable-disable-smbv1-smbv2-smbv3-in-windows-and-windows-server

# Mounting a samba share in windows 10
Doesn't need to be admin (if you do it as admin, regular users can't see it).
neither user nor password need to be valid.

```
net use \\10.0.0.4\disks /user:test abc
```

# Mounting a Bitlocker Disk in Linux
Note to boot into linux on thinkpad had to disable secure boot and allow legacy boot.  Otherwise it sees usb but ignores.
Supposedly there's a utility to make UEFI linux bootable sticks but  I haven't tried.

```text
sudo apt-get install gcc cmake make libfuse-dev libmbedtls-dev ruby-dev
git clone https://github.com/Aorimn/dislocker.git /tmp/dislocker

cd /tmp/dislocker
cmake .
make
sudo make install

dislocker -r -V /dev/sda1 -p315442-000000-000000-000000-000000-000000-000000-000000 -- /media/windows (replace your own bitlocker key and source partition)
mount -o loop dislocker-file /media/mount
```

# Windows AD Hacking

https://github.com/mantvydasb/RedTeam-Tactics-and-Techniques/tree/master/offensive-security-experiments/active-directory-kerberos-abuse

# GPO to turn of screen lock

```text
Edit Group Policies
Computer Config -> Admin Templates -> System -> Power Management > Video and Display Settings -> Turn off the Display
Enable, and set time to 0

gpupdate /force
```

# Disable Spectre Mitigations

 To disable mitigations for CVE-2017-5715 (Spectre Variant 2) and CVE-2017-5754 (Meltdown)
```
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v FeatureSettingsOverride /t REG_DWORD /d 3 /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v FeatureSettingsOverrideMask /t REG_DWORD /d 3 /f 
```

# Scripted FTP
```
echo open 192.168.1.101 21> ftp.txt
echo USER asshat>> ftp.txt
echo mysecretpassword>> ftp.txt
echo bin>> ftp.txt
echo GET wget.exe>> ftp.txt
echo bye>> ftp.txt
```

And then
```
ftp -v -n -s:ftp.txt
```

# TFTP
up to windows 2003
```
tftp -i 192.160.1.101 GET wget.exe
```






