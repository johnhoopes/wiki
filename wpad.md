<!-- TITLE: Wpad -->
<!-- SUBTITLE: A quick summary of Wpad -->

# DNS
# WINS
# NMB
# DHCP Response
Per Cisco site (https://www.cisco.com/c/en/us/td/docs/security/web_security/connector/connector2972A/WPADAP.html):  
A browser that supports both methods will check the DHCP assignment first, before attempting the DNS method.

A DHCP server must be configured to serve an additional setting in an IP address assignment; option 252. This option specifies the exact location of the PAC file. The file name does not need to follow any specific naming convention, however if WPAD DNS is to be used also, the file must have the file name wpad.dat.

A Web browser implementing this method sends the DHCP server a DHCPINFORM query, the DHCP server will return the expected IP settings along with the 252 option which defines the location of the PAC file. The browser will then download this PAC file from the URL provided. 

Can DHCP Response be sent unsolicited?
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

# Hash Collection using WPAD
responder does this.  Should upgrade python server to only request it once per machine.  Once I've got it, don't require it.  Also research which processes will provide it.  Windows Update?  Adobe?



