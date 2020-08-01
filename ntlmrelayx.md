<!-- TITLE: Ntlmrelayx -->
<!-- SUBTITLE: A quick summary of Ntlmrelayx -->

# Note that as of this writing it uses python 2.7.18
use pipenv to install in a clean env

# Common Usages
## No Arguments defaults to dumping SAM
```
ntlmrelayx.py -tf targets -w --no-http-server -smb2support
-tf uses a target file instead of one target
-w means to watch the target file in case it changes.
Targetfile should be ldap://ip   smb://ip  https://ip etc
```