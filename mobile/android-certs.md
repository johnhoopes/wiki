---
title: Android Certs
description: A quick summary of Android Certs
published: true
date: 2023-03-08T21:03:11.211Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:29:52.057Z
---

# From Jimmy's notes.... untested
Install Burp CA Cert into device when above doesn't work
	(when Settings -> Security -> Install from Storage (DER, PEM or PKCS12 stupid fucking bugs) does not work):
		/system directory is read-only, you must remount:
			adb shell
			mount -o rw,remount /system
			#mount -o ro,remount /system #to put it back
			try push command above again
		Export Portswigger CA cert from Firefox as PEM file
		rename file to 9a5ba575.0
		copy to Android device (must use this!! can NOT copy from sdcard):
			push 9a5ba575.0 /system/etc/security/cacerts/	
			
		/system directory is rebuilt with each reboot of device.  Therefore,
		you must perform the steps above every time you want to use it.
		you can make sure it shows up in the “Trusted Credentials”
			Settings -> Security -> Trusted Credentials - CA Certs
		Another method:
		Export Cert from Burp:
			Proxy -> Options -> CA Certificate... -> Certificate in DER format -> Name it PortSwigger.der
		openssl x509 -inform DER -subject_hash_old -in PortSwigger.der
		copy cert into burp.cer
		cat burp.cer > 5ed36f99.0 (5ed36f99 is value that showed up at the top of the previous command)
		openssl x509 -inform PEM -text -in burp.cer -out /dev/null >> 5ed36f99.0
		
    
# Another method that has been tested on TCL phone (not persistent; have to do every reboot)

1. Get Burp cert and conver to PEM format (with  ---Begin Cert--) etc.
2. Get the hash using following command
```
openssl x509 -in burp.cer -subject_hash_old | head -n -1
```
Mine resulted in 9a5ba575 (same as above).
3. copy file to hash.0
```
cp burp.cer 9a5ba575.0
```
4. adb shell and get root (/data/local/tmp/mtk-su)
5. Make a temp dir to store current certs. (not sure perms are important but it worked, so I'm keeping it).
```
mkdir -m 700 /data/local/tmp/certs
```
6. Copy existing certs to temp spot.
```
cp /system/etc/security/cacerts/* /data/local/tmp/certs/
```
7. Make a temporary filesystem overlaying the existing certs
```
mount -t tmpfs tmpfs /system/etc/security/cacerts/
```
8. Copy existing certs to tmp filesystem.
```
cp /data/local/tmp/certs/ /system/etc/security/cacerts/
```
9. Copy your cert to tmp filesystem.
```
cp /data/local/tmp/9a5ba575.0 /system/etc/security/cacerts/
```
10. Fix the perms
```
chown root;root /system/etc/cacerts/*
chmod 644 /system/etc/security/cacerts/*
chcon u:object_r:system_file:s0 /system/etc/security/cacerts/*
```
Check Settings->"Security & location"->"Encryption & credentials"->"Trusted Credentials"->System  for Portswigger

11. Profit
