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
ssh -D 12344 -J me@jumphost root@unreachable-host
```

# Proxy Command
```
ssh -o ProxyCommand="ssh -W %h:%p bob@10.10.10.10" bob@remote
```