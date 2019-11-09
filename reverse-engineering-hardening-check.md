<!-- TITLE: Reverse Engineering Hardening Check -->
<!-- SUBTITLE: A quick summary of Reverse Engineering Hardening Check -->

```
apt install devscripts
hardening-check full-troll

full_troll:
 Position Independent Executable: yes
 Stack protected: yes
 Fortify Source functions: no, only unprotected functions found!
 Read-only relocations: yes
 Immediate binding: yes
 
```