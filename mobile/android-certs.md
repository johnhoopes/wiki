<!-- TITLE: Android Certs -->
<!-- SUBTITLE: A quick summary of Android Certs -->

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
		