<!-- TITLE: Wpad -->
<!-- SUBTITLE: A quick summary of Wpad -->

# DNS
# WINS
# NMB
# Windows Command to show proxy
```
netsh winhttp show proxy
```
# DHCP Response
Per Cisco site (https://www.cisco.com/c/en/us/td/docs/security/web_security/connector/connector2972A/WPADAP.html):  
A browser that supports both methods will check the DHCP assignment first, before attempting the DNS method.

A DHCP server must be configured to serve an additional setting in an IP address assignment; option 252. This option specifies the exact location of the PAC file. The file name does not need to follow any specific naming convention, however if WPAD DNS is to be used also, the file must have the file name wpad.dat.

A Web browser implementing this method sends the DHCP server a DHCPINFORM query, the DHCP server will return the expected IP settings along with the 252 option which defines the location of the PAC file. The browser will then download this PAC file from the URL provided. 

Can DHCP Response be sent unsolicited?

# isc-dhcp-server
How to configure isc-dhcp-server to send option...

```
option local-proxy-config code 252 = text;

subnet 1.1.1.0 netmask 255.255.255.0 {
  range 1.1.1.128 1.1.1.254;
  option domain-name-servers 1.1.1.1;
  option domain-name "wb.local";
  option subnet-mask 255.255.255.0;
  default-lease-time 600;
  max-lease-time 7200;
  option local-proxy-config "http://1.1.1.1/wpad_dhcp.dat";
}
```

# Example Response

```text
function FindProxyForURL(url, host) {
        return "PROXY 10.0.0.169:8080";
}
```

# Example Python Server (note content-type)

```text
import SimpleHTTPServer
import SocketServer
import logging

PORT = 80


class GetHandler(SimpleHTTPServer.SimpleHTTPRequestHandler):

    def do_GET(self):
        logging.error(self.headers)
        SimpleHTTPServer.SimpleHTTPRequestHandler.do_GET(self)

Handler = GetHandler

Handler.extensions_map.update({
    '.dat': 'application/x-ns-proxy-autoconfig',
});

httpd = SocketServer.TCPServer(("", PORT), Handler)

print "serving at port", PORT
httpd.serve_forever()

```

# Configuring apache to use php for .dat files
The following goes in php7.x.conf (note that php has to be enabled).
```
<FilesMatch ".+\.dat$">
  SetHandler application/x-httpd-php
</FilesMatch>
```

# Hash Collection using WPAD
responder does this.  Should upgrade python server to only request it once per machine.  Once I've got it, don't require it.  Also research which processes will provide it.  Windows Update?  Adobe?

# Things to Try
* Want list of software that honors WPAD.  DHCP, DNS, and WINS
	* Collect User-agent
	* how many times does each piece try?
		* Which one is actually used?
	* Caching?
* All software needs to try all tests
* Will need base64-encoding function for leak encoding
* Tests - To be done inside FindProxyForURL and outside
	* Alert()
	* Divide by zero
	* Namespace exploration
	* dns resolution to indicate execution
	* infinite loop
	* infinite recursion
	* spectre stuff for external examination
	* Does js have exception handling?
	* explore built in function implementation (looking for leaks)
