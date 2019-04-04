<!-- TITLE: Openssh -->
<!-- SUBTITLE: A quick summary of Openssh -->

# Resuming an SCP transfer
```
rsync -e ssh \
--partial --append \
--progress \
remote.example.org:/path/to/file .
```