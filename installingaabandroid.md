<!-- TITLE: Installing an aab file on android -->
<!-- SUBTITLE: A quick summary of Installing aab on android -->

# Get Bundletool
github.com/google/bundletool/releases

# Make a keystore if you don't have one 
```
keytool -genkey -v -keystore hoopes.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
```

# Convert aab to apks file
```
java -jar bundletool-all-1.8.2.jar build-apks --bundle=aab_to_convert.aab --output=aab_to_convert.apks --ks=hoopes.keystore --ks-pass pass:password --ks-key-alias=alias_name
```

# Install apks file
```
java -jar bundletool.jar install-apks --apks=aab_to_convert.apks
```

Note that it didn't appear on the desktop like a normal installation, but was in the list of apps.
