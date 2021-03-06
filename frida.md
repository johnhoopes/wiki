<!-- TITLE: Frida -->
<!-- SUBTITLE: A quick summary of Frida -->

# Installation
```
pip install frida
pip install frida-tools
```

Then you need a frida-server installed on the device.  Grab that here.... https://github.com/frida/frida/releases
Note that x86 or x86_64 depends on the processor of emulator (mine is x86 for now)

```
adb root # might be required
adb push frida-server /data/local/tmp/ 
adb shell "chmod 755 /data/local/tmp/frida-server"
adb shell "/data/local/tmp/frida-server &"
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

# Python interfacing with a running process
```
import frida
import time
device = frida.get_usb_device()
pid = device.spawn(["com.fugu.baskinrobbins"])

device.resume(pid)

time.sleep(5)

session=device.attach(pid)

script = session.create_script(open("universal-ssl-check-bypass.js").read())

script.load()

input()
```

# Javascript example of hooking function 
From https://11x256.github.io/Frida-hooking-android-part-1/
```
console.log("Script loaded successfully ");
Java.perform(function x(){ //Silently fails without the sleep from the python code
    console.log("Inside java perform function");
    //get a wrapper for our class
    var my_class = Java.use("com.example.a11x256.frida_test.my_activity");
    //replace the original implmenetation of the function `fun` with our custom function
    my_class.fun.implementation = function(x,y){
    //print the original arguments
    console.log( "original call: fun("+ x + ", " + y + ")");
    //call the original implementation of `fun` with args (2,5)
    var ret_value = this.fun(2,5);
    return ret_value;
    }});
```

my_activity is one of the java classes.
fun() is the function to be hooked

# Overloaded Function Hooking
```
my_class.fun.overload("int" , "int").implementation = function(x,y){ //hooking the old function

....

my_class.fun.overload("java.lang.String").implementation = function(x){ //hooking the new function
```


# JS to Iterate through functions in an activity
Java.choose("com.example.a11x256.frida_test.my_activity", {
                onMatch: function (instance) {
                    console.log("Found instance: " + instance);
                    instances_array.push(instance)
                    console.log("Result of secret func: " + instance.secret());
                },
                onComplete: function () { }

            });
						

# Highlights of Frida Python
## Device
spawn - start a process
attach - attach to running process
disable_spawn_gating
enable_spawn_gating
enumerate_applications - don't know yet
enumerate_pending_children
enumerate_pending_spawn
enumerate_processes
get_frontmost_application
get_process
icon
id
inject_library_blob
inject_library_file
input
kill
name
off
on
open_channel
resume
spawn
type

## Session
compile_script - 
create_script -
create_script_from_bytes
detach
disable_child_gating
disable_debugger
enable_child_gating
enable_debugger
enable_jit
off
on
