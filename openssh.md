<!-- TITLE: Openssh -->
<!-- SUBTITLE: A quick summary of Openssh -->

# Resuming an SCP transfer
```
rsync -e ssh \
--partial --append \
--progress \
remote.example.org:/path/to/file .
```

# Using a Jumphost
```
ssh -D 12344 -J john.hoopes@xfr-rpt-jumphost root@na-vm0353-pt
```

# Proxy Command
```
Need to look this up again
```