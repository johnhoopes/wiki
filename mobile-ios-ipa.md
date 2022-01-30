<!-- TITLE: Mobile Ios Ipa -->
<!-- SUBTITLE: A quick summary of Mobile Ios Ipa -->

# IPA file is gone, but you can still find .app file in

```
/private/var/containers/Bundle/Application/
```

And data lives in 
```
/private/var/mobile/Containers/Data/Application
```


# Found a way to get an IPA file.  Probably not enough but better.

https://medium.com/xcnotes/how-to-download-ipa-from-app-store-43e04b3d0332

On computer:
1. Install frida
```
$ pip3 install frida-tools
```

2. Install frida-ios-dump
```
$ git clone https://github.com/AloneMonkey/frida-ios-dump.git
$ cd frida-ios-dump
$ pip3 install -r requirements.txt --upgrade
```

3. Open a new Terminal window and pull decrypted .ipa:
```
$ cd frida-ios-dump
$ python3 dump.py -H 10.0.0.173 -u root -P HateApple! 'PackageName' -p 22
```

For some reason the -L (to list packages) only worked when device was connected to USB.

# Installing IPA without store
I was able to open ipa (zip), take .app directory.  Copy it to phone using scp.  mv .app directory to /Applications and respring


# Respring
```
sbreload
```

# frida-trace
```
frida-trace -U -F  (trace the foreground process)
```

Hook the MMEMethods
```
frida-trace -U -F -m '+[MMEMethods *]' 
```