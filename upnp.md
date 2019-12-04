<!-- TITLE: Upnp -->
<!-- SUBTITLE: A quick summary of Upnp -->

# Structure
Http over UDP to broadcast addr on port 1900
Response is xml with urls for icon and service

# Tool
found ssdp server somewhere

Following implements a simple test device.

```
#!/usr/bin/python

from ssdp import SSDPServer
import uuid

device_uuid = uuid.uuid4()
local_ip_address = '10.0.0.4'

ssdp = SSDPServer()
ssdp.register('local',
              'uuid:{}::upnp:rootdevice'.format(device_uuid),
              'upnp:rootdevice',
              'http://{}:8088/jambon-3000.xml'.format(local_ip_address))
ssdp.run()
```

# Attack 1 - NTLM Query
Can you get a windows box to authorize in order to get 1900 data?
What about picture?
What about service data?
What about url's in service data?

# Attack 2 - XML Attacks
XXE -
Recursive stuff

# Javascript -
Will it be parsed?

# 302 Redirects get followed?

