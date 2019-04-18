<!-- TITLE: Frida -->
<!-- SUBTITLE: A quick summary of Frida -->

# Installation
```
pip install frida
pip install frida-tools
```

Then you need a frida-server installed.  Grab that here.... https://github.com/frida/frida/releases
Note that x86 or x86_64 depends on the processor of emulator (mine is x86 for now)

```
$ adb root # might be required
$ adb push frida-server /data/local/tmp/ 
$ adb shell "chmod 755 /data/local/tmp/frida-server"
$ adb shell "/data/local/tmp/frida-server &"
```


# PS Listing
```
frida-ps -U
```

# Frida Script to ignore SSL validation issues 
(save below as universal-ssl-check-bypass.js)
```
Java.perform(function() {                
 
    var array_list = Java.use("java.util.ArrayList");
    var ApiClient = Java.use('com.android.org.conscrypt.TrustManagerImpl');
 
    ApiClient.checkTrustedRecursive.implementation = function(a1,a2,a3,a4,a5,a6) {
            // console.log('Bypassing SSL Pinning');
            var k = array_list.$new(); 
            return k;
    }
 
},0);
```

Using the script to start an app hooked.
```
jhoopes@LAPTOP-H5S9KB5I:~$ frida -U -f com.seic.swp.penntrust -l universal-ssl-check-bypass.js --no-pause
```