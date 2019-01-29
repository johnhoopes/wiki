<!-- TITLE: Msfdb -->
<!-- SUBTITLE: A quick summary of Msfdb -->

# Loading RHOSTS with a db query result
msf > services -p 445 -R

Services
 ------------

host           port  proto  name          state  info
----           ----  -----  ----          -----  ----
192.168.1.10   445   tcp    microsoft-ds  open   Samba smbd 3.X workgroup: SKYNET
192.168.1.9    445   tcp    microsoft-ds  open

 RHOSTS => file:/tmp/msf-db-rhosts-20110909-32464-oyzbko

Looks the same as before, but by adding the -R flag, you’ve told Metasploit to set the RHOSTS variable to the output of the database query you’ve just performed. This is reflected in the last line of output which is the filename of the hosts that you’ve selected from the database which Metasploit created and populated.
Now select an exploit to use against these hosts
